# QA_Automation
This is where all of the scripts, setup, test data, and all fun things QA are stored.

## QA Automation
This document will tell you how to set up a QA test environment and give you everything you need to start scripting. 

### Environment: 

Electron is a framework for creating native applications with web technologies like JavaScript, HTML, and CSS.
Mocha is a JavaScript test framework which runs on Node.js. Mocha allows us to use any assertion library we like. 
Chai is a BDD/TDD assertion library for Node.js. We will be using Chai As Promised.
Spectron is an open source framework for easily writing automated integrations and end-to-end tests for Electron. 

The text editor I use to write my scripts is Sublime 3. There are plenty other options out there. 


### Setup: 

Always first setup a directory somewhere on your desktop, to store all of your automation scripts, files, dependancies, etc. 

Homebrew is a missing package manager. To install, just throw this command in Terminal `/usr/local`.


    ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

 
 Now that we have Homebrew, let’s go install `npm` via Terminal:
 `$ brew install node`
 
 We will have to install Spectron, Chai, Chai as Promised, Mocha, @types/Mocha, and Electron-Chromedriver as  development dependencies:

    npm install --save-dev spectron
    npm install --save-dev chai
    npm install --save-dev chai-as-promised
    npm install --save-dev mocha 
    npm install --save-dev electron-chromedriver
    npm install --save-dev @types/mocha

Finally, your `devDependencies` in your `package.json`  file should look like this (perhaps with newer version numbers):

    "devDependencies": {
       "@types/mocha": "2.2.43",
       "chai": "4.1.2",
       "chai-as-promised": "7.1.1",
       "electron-chromedriver": "1.7.1",
       "mocha": "3.5.3",
       "spectron": "3.7.2"
    }

Setting Up the Mocha Test Runner
Next, we go to our `package.json` file to set up the test commands. A minimal configuration calls the Mocha test runner without any parameter settings.

    "scripts": {
        "test": "mocha"
    }

When you run a test via  `npm run test`, Mocha is executed looking for unit tests or integration tests. 

The following command tells Mocha to only run tests contained at a specific location. The `grep` command tells it to only consider files with a certain file name. The `--watch` parameter runs tests on changes to JavaScript files in the defined directory and once initially.

    mocha {{folder/with/tests}} --grep {{^regex$}} --watch
