# Introduction of Repository

This repository contains code and test instructions of how to build NPM package and publish and test NPM package. 

# Introduction of NPM package

NPM is a Node Package Manager which are extensively used for Node.js packages. Package is a set of files which need for a module or application.

# Installation of NPM package

If you have installed Node.js, NPM would have installed by default. If not, Here is a link to install [Node.js](https://nodejs.org/en/)

Note : Its good and recommended to go with LTS ( Long term support) version of node.js

To check if npm is enabled, Open your terminal and enter `npm --version` and you will get some version of npm like this

### Output

```
viswg@udcdjncda4a85d:~/codezen$ npm --version
6.12.0
```
# Creating JSON file

Due to the simplisit nature of the NPM, Most of the code is run through CLI. Open your terminal and create a new directory.
### Output

```
# Create the project directory
mkdir pick-random-number  # Create new directory
cd pick-random-number     # Change into the project directory
```
Once new directory is created and you're in new project directory. Now we will intialize an NPM package in current directory. 
### Output

```
npm init                       # Initialise an NPM package
```

Once `npm init` is given, it should open an interactive session in CLI that look like this, 
### Output

```
viswg@uef1b5fa2a4a85d:~/codezen/test/pick-random-number$ npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help json` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
```
You will be required to answer some questions which are mostly about the NPM package which you're going to create. The command line tool auto-suggests reasonable answers to the questions, if you feel the suggested answer is good enough, just hit enter. If you also don’t have an answer to any of the question, hit enter and continue, you can always edit it later.
### Output

```

package name: (pick-random-number) 
version: (1.0.0) 
description: Package to pick any random numbers
entry point: (index.js) 
test command: 
git repository: 
keywords: random numbers
author: gowtham
license: (ISC) 
About to write to /home/viswg/codezen/test/pick-random-number/package.json:
```
Once you have created, Your json file should look like this :
### Output
```

{
  "name": "pick-random-number",
  "version": "1.0.0",
  "description": "Package to pick any random numbers",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [
    "random",
    "numbers"
  ],
  "author": "gowtham",
  "license": "ISC"
}


Is this OK? (yes) yes              #Hit 'yes'
```

Package.json is the single and most important file as far as creating/publishing an NPM package is concerned, without it, you won’t be able to publish whatever you create to the NPM registry.

Note the main field in the package.json file, it refers to the name of the file that would be loaded when your package is required by another application, by default it points to `index.js`

# Creating project codes

The project to be created is a very simple one, in fact, all the project code will be composed in a single file.

Create an `index.js` file in the root of the project folder, Your file directories should look like this :

### Output
```
viswg@ueskcsdklc2a4a85d:~/codezen/Master$ ls
index.js  pick-random-number
viswg@ueskcsdklc2a4a85d:~/codezen/Master$ cd pick-random-number/
viswg@uef1cdjsdkca4a85d:~/codezen/Master/pick-random-number$ ls
package.json
```

Then add the code for the random number generator in `index.js` file:
### Input

```
function randomNoGenerator(min, max) {
  if(typeof(max) !== 'number' && typeof(min) !== 'number') {
    min = 0;  max = 1;
  }
 return (Math.random() * (max-min)) + min;
}module.exports = randomNoGenerator;
```
Notice the module.exports at the bottom of the file, whatever you are exporting here is what would be available for importing when others install the package.
Your package is now ready to publish at [NPM website](https://www.npmjs.com/)

# Publishing the package

## Few thing to check before publishing the package :

1. Check if your package name is different than existing packages in [NPM website](https://www.npmjs.com/) . If its not, Its time to change your package name.
2. You need to create an account in the NPM registry, you can do this [here](https://www.npmjs.com/signup)
3. Once you have created account, sign in and verify your NPM account from your email address.
4. Open your terminal and type the `npm login` you will be prompted to enter the username , email address and password. 
5. To check you have validated the account correctly, enter ` npm whoami` .You will see your account name in output.
### Output

 ```
    viswg@uef1b5fa2a4a85d:~/codezen/Master/pick-random-number$ npm whoami
    gowtham-viswa
 ```
 
Publish your NPM package using command `npm publish` your terminal output should look like this :

### Output

```
    viswg@uef1b5fa2a4a85d:~/codezen/test/pick-random-number$ npm publish
    npm notice 
    npm notice 📦  pick-random-number@1.0.0
    npm notice === Tarball Contents === 
    npm notice 304B package.json
    npm notice === Tarball Details === 
    npm notice name:          pick-random-number                      
    npm notice version:       1.0.0                                   
    npm notice package size:  293 B                                   
    npm notice unpacked size: 304 B                                   
    npm notice shasum:        c1f49d006213a0e3029823ca7e6223f77ebb6fb8
    npm notice integrity:     sha512-5YtM1Um8Q2GhV[...]7pvVk6JyN8jaA==
    npm notice total files:   1                                       
    npm notice 
    + pick-random-number@1.0.0
 ```
  It's done. You have published your npm package.
  
  Your package is now visible in [NPM Packages](https://www.npmjs.com/search?q=pick-random-number)
  
# Testing the published NPM Package
  
  To test the package, you simply need to install and use it. You can do the following to test the `pick-random-number` [package] (https://www.npmjs.com/package/pick-random-number) and follow the below steps : 
  
  1. Create a test directory
  2. Change into test directory
  3. Download the test file from test directory and paste in current directory.
  4. Install `pick-random-number` [package] (https://www.npmjs.com/package/pick-random-number) from npm website.
  
Your terminal should look like this :
  
```
viswg@uef1b5fa2hja4a85d:~/codezen$ mkdir test-random
viswg@uef1b5fa2a4a85d:~/codezen$ cd test-random/
viswg@uef1b5fa2a4a85d:~/codezen/test-random$ npm install pick-random-number --save

```
Now run the `test.js` file in command line using below code :

```

viswg@uef1b5fa2a4a85d:~/codezen/test-random$ node ./test.js
46
viswg@uef1b5fa2a4a85d:~/codezen/test-random$ node ./test.js
47
viswg@uef1b5fa2a4a85d:~/codezen/test-random$ node ./test.js
79
viswg@uef1b5fa2a4a85d:~/codezen/test-random$ node ./test.js
55
viswg@uef1b5fa2a4a85d:~/codezen/test-random$ node ./test.js
85
viswg@uef1b5fa2a4a85d:~/codezen/test-random$ node ./test.js
71
```
