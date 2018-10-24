# How to: [bit  (bitsrc)](https://bitsrc.io/) - Practical Examples
## What is bit?
From [bit's official website:](https://bitsrc.io/)
>Bit helps you organize your components, share them as a team and keep them synced in all your projects.

The idea is to be able to export some pieces of code that you're gonna use often and that don't really need to have their source code modified in order to make your project work.  
These pieces of code are called components.

Let's say you're working on a styleguide component to display all your ui elements. This component should be able to take parameters (props, options, ...) and render/export a styleguide from there. 
Whether that component is for Node, React/Vue or just Vanilla JS, you'll probably want to import it on other projects.
  
Bit can help you in a few ways by allowing you to:  
* **Export your component** to a remote scope (a bit like git (pun intended))
* **Keep a version** of your component 
    * Allows you to lock a component to a single version
    * Allows you to update your component on any project
* **Document your component** with a README.md or JSDoc
* **Build your component** which allows you to use them in any environment (e.g: compile .vue files to .js)
* **Test your component** and see on your component's page all your written tests
* **Preview your component** and see what your component should look like in some Front-End Frameworks (React, Vue, ...)
* **Import your component** with NPM, Yarn or bit

This guide will complete some of the misconception you could have when starting bit for the first time.

## Installing bit
### NPM
```console
npm install bit-bin -g
```

## Initializing bit in your project
```console
bit init
```
## [Isolating and Tracking Components](https://docs.bitsrc.io/docs/isolating-and-tracking-components.html)
>Tracking subsets of files as components separates their representation from the repository’s file system.

To track a file/folder use [bit add](https://docs.bitsrc.io/docs/cli-add.html).  
A tracked component it must have at least a main file, and id.  
Even though the id argument is optional, it is a good idea to always include one.

### Adding a file:
```console
bit add path/to/file.js --id component-theme/component-name
```
In this case, file.js is automatically the main file and its id will be component-theme/component-name.  

**Practical Example:**
```console
bit add webpack-extension/css-comment-parser-webpack-plugin.js --id webpack/css-comment-parser-plugin
```

### Adding a folder:
```console
bit add path/to/folder --main path/to/folder/file.js --id component-theme/component-name
```
In this case, the whole folder will be part of the component and the main file must be specified.  

**Practical Example:**
```console
bit add webpack-extension --main webpack-extension/css-comment-parser-webpack-plugin.js --id webpack/css-comment-parser-plugin
```

## [Versioning Components](https://docs.bitsrc.io/docs/versioning-tracked-components.html)
>Versioning tracked components in a repository helps create a higher-level contracts, for the safe reuse of components between different repositories and users.

To version a newly added/modified component use [bit tag](https://docs.bitsrc.io/docs/cli-tag.html).  
###Tagging a Component:
```console
// tag all added components automatically
bit tag --all
// or tag all added components with a specific version
bit tag --all 0.0.1
// or tag a single component with a specific version
bit tag component-theme/component-name 0.0.1
```
**Practical Example:**
```console
bit tag webpack/css-comment-parser-plugin 0.0.1
```
### Exporting a Component:
```console
bit export yourusername.yourscopename
```
**Practical Example:**
```console
bit export wurielle.pristine
```
>**NOTE:** To add a compiler/tester AFTER your component has been exported please refer to
