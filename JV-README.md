#Continuous Integration with Travis CI

###Getting Started

```
cd MyDevelopment/github/thinkful
git clone https://github.com/Thinkful-Ed/node-shopping-list-integration-tests.git

cd node-shopping-list-integration-tests
```
created new repo on github:
node-shopping-list-integration-tests

change to new remote:

```
git remote set-url origin https://github.com/johnvincentio/node-shopping-list-integration-tests
```

Push the master branch up to your new repo on GitHub:

```
git push -u origin master
```

Install dependencies:

```
npm install
```

To run the tests:
```
npm test
```

##Travis CI
https://travis-ci.org/

1. Sign-up
	* Authorize, give lots of privileges
	* Travis syncs projects

2. From github
	* Select node-shopping-list-integration-tests project
	* Settings, Integrations & services (left menu)
	* Add a Service (mid-right)
		* Select Travis CI from dropdown
		* Add service(green button at bottom)
	* From Travis CI, click on <username>(top right)
		* Lists github projects
		* Activate node-shopping-list-integration-tests
	* From github, repository node-shopping-list-integration-tests
		*  Settings, Integrations & services
			* Travis CI, Edit
				* Notice Travis CI entry in Webhooks

3. Create .travis.yml

```
cd github/node-shopping-list-integration-tests
touch .travis.yml
```
Code in .travis.yml

```
language: node_js
node_js: node
```

Git .travis.yml to master

4. From Travis CI
	* Select node-shopping-list-integration-tests
	* Travis builds the project, see Job log
	* When complete, Restart build appears (mid-right)

##Set up continuous deployment
* Configure Travis to work with Heroku. 
* Push changes to master on GitHub, or merge a pull request into master, our tests automatically run.
	* If our tests pass, TravisCI will deploy to Heroku. If our tests do not pass, it will not deploy.

1. Install Travis CI command line interface
```
sudo gem install travis
```

2. Setup Travis to Deploy to Heroku
Travis login requires my github login.

```
cd node-shopping-list-integration-tests
travis login
```

To deploy to Heroku:

	* travis setup heroku
		* "return" to the questions.
	* git diff (see differences)
 
3. Create app on Heroku

```
heroku create
```

Notice:

	* App name: still-beyond-62965
	* https://still-beyond-62965.herokuapp.com/
	* https://git.heroku.com/still-beyond-62965.git


Edit .travis.yml

```
deploy:
	app: still-beyond-62965
```

4. Git commit changes to master

To run the app on Heroku:

```
https://still-beyond-62965.herokuapp.com/
```

###Test CI is working
Change any file, git commit to master and verify Travis CI rebuilds the project.

###Other:
git remote -v
shows github and heroku repositories.


