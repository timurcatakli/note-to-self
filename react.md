##Setting Up the Project

Webpack is one of those tools that depends on Node.js. Make sure you have it installed and that you have npm available at your terminal. Set up a directory for your project, navigate there, execute npm init, and fill in some details. You can just hit return for each and it will work. Here are the commands:
```
mkdir kanban_app
cd kanban_app
npm init -y # -y gives you default *package.json*, skip for more control
```

### Setting Up Git
If you are into version control, as you should, this would be a good time to set up your repository. You can create commits as you progress with the project.

If you are using git, I recommend setting up a .gitignore to the project root: .gitignore
```
node_modules
```

### Installing Webpack
Next, you should get Webpack installed. We'll do a local install and save it as a project dependency. This will allow us to maintain Webpack's version per project. Execute
```
npm i webpack --save-dev
```

Try executing Webpack from there through terminal using **node_modules/.bin/webpack** or a similar command.

Directory Structure
As projects with just package.json are boring, we should set up something more concrete. To get started, we can implement a little web site that loads some JavaScript which we then build using Webpack. Set up a structure like this:

/app
--  index.js
--  component.js
/build
--  index.html
/package.json
/webpack.config.js

In this case, we'll generate bundle.js using Webpack based on our /app. To make this possible, we should set up some assets and webpack.config.js.

### Setting Up Webpack Configuration
We'll need to tell Webpack how to deal with the assets we just set up. For this purpose we'll develop a webpack.config.js file. Webpack and its development server will be able to discover this file through convention.

To map our application to build/bundle.js we need configuration like this:

webpack.config.js
```
const path = require('path');

const PATHS = {
  app: path.join(__dirname, 'app'),
  build: path.join(__dirname, 'build')
};

module.exports = {
  // Entry accepts a path or an object of entries. We'll be using the
  // latter form given it's convenient with more complex configurations.
  entry: {
    app: PATHS.app
  },
  output: {
    path: PATHS.build,
    filename: 'bundle.js'
  }
};
```
The entry path could be given as a relative one. The context field can be used to configure that lookup. Given plenty of places expect absolute paths, I prefer to use absolute paths everywhere to avoid confusion.
