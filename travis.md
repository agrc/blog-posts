#How to Wire up Travis-CI to your JS Projects

For the past six months, AGRC has been using [Travis CI](https://travis-ci.org) to automatically test and lint our projects each time we push a commit to the associated GitHub repository. Even though we run these tasks locally it's been helpful to have them run on Travis for when we miss things. It's also a major step towards automated deployments as well as running our tests via something like [Sauce Labs](https://saucelabs.com) or [Browser Stack](http://www.browserstack.com/).

###travis-ci.org
The set up is relatively simple. The first step is to sign into [travis-ci-.org](https://travis-ci.org) with your [GitHub](https://github.com) account. Once you're signed in you can go to your accounts page and see all of the GitHub repositories associated with your account. Switching a repository to "ON" tells Travis-CI to start watching any new commits that you push to that repository.

![accounts page](http://i.imgur.com/cj0bkMk.png)

### .travis.yml
The next step is to let Travis-CI know what you want it to do. The first part of this step is accomplished by creating a [`.travis.yml` file](http://docs.travis-ci.com/user/build-configuration/) at the root of your project. Here's an example from one of our projects:

```yml
language: node_js
node_js:
  - '0.10'
before_install:
  - npm install -g grunt-cli
  - npm install -g bower
  - npm install
  - bower install
notifications:
  email:
    on_success: never
```

The lines below `before_install` load all of the project dependencies via npm & Bower. The notifications code just tells Travis to only send us emails when a build fails.

### package.json
The second part to defining what you want Travis-CI to do is to add a `scripts` property to the your `package.json` file for your project. Travis-CI automatically runs `npm test` for NodeJS projects. Adding this new property to `package.json` defines this command. We use a special `travis` [GruntJS](http://gruntjs.com/) task to run tasks so this is the command for us:
```json
"scripts": {
    "test": "grunt travis -v"
} 
```

The `travis` grunt task can contain any sub-tasks that you want. Here's what ours looks like:
```javascript
grunt.registerTask('travis', [
    'if-missing:esri_slurp:travis',
    'jshint',
    'connect',
    'jasmine:app',
    'build-prod'
]);
```

### Build Status Badge
The icing on the cake is to copy code from Travis-CI to your app's `README.md` to show a "build:passing" or "build:failing" (gasp!) badge. You can do this by going to your project's page on travis-ci.org and clicking on the badge in the upper right-hand corner of the page.

### GitHub.com Integration
After getting everything wired up you'll notice that pull requests automatically display the build status of each commit and will let you know if it is still waiting on a build to run.

![still waiting](http://i.imgur.com/6uvXjrH.png)

![good to go](http://i.imgur.com/kVF1ny4.png)

If you want to see all of this in action you can checkout the [AGRCJavaScriptProjectBoilerPlate](https://github.com/agrc/AGRCJavaScriptProjectBoilerPlate) repository.
