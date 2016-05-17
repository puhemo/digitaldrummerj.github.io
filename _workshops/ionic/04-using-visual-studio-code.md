---
collection: workshops
title: 'Lab 04: Using Visual Studio Code'
published: true
type: ionic
layout: workshoppost2
order: 4
lab: ionic
length: 10 minutes
date: 2016-05-16
todo: |
---

{% assign imagedir = "../images/project-layout/" %}


{:.fake-h2}
Objective


Visual Studio Code out of the box has good default settings to immediately start using it as an editor.  To make it even more effective to use Visual Studio Code there are a few extensions for angular and ionic that you will want to install.  As well there are a few shortcuts and settings that come in handy.


>**Note**: If you don't already have Visual Studio Code installed see [Lab 01: Ionic Setup](../01-install-ionic/)

{:.fake-h2}
Table of Contents

* TOC
{:toc}

## 4.0: Shortcuts

**Key Shortcuts**

* Toggle Sidebar: ctrl+b
* Go to File: ctrl+p or ctrl+e (both seem to work)
* Split Editor: ctrl+\
* Switch to Editor Page: ctrl+[pane #]
* Close active page: ctrl+w or ctrl+f4
* Navigate Between Open Files: ctrl+tab
* Format Code: Shift+Alt+F
* Toggle Commenting Out Line: ctrl+k, ctrl+c
* Open Command Prompt: ctrl+shift+c
* Toggle Word Wrap: alt+z

**Nice to Have If you Remember Them**
* Command Palette: F1 or Ctrl+Shift+P
* Code Fold: ctrl+shift+[
* Code Unfold: ctrl+shift+]

## 4.1: My settings

Here are my settings that I use for Visual Studio Code.  You can edit these by going under File -> Preferences -> User Settings

    {
        "editor.tabSize": 5,
        "editor.wrappingColumn": 0,
        "editor.autoClosingBrackets": true,
        "editor.formatOnType": true,
        "editor.detectIndentation": true,
        "editor.wrappingIndent": "indent",
        "files.exclude": {
             "**/.git": true,
            "**/.DS_Store": true,
            "**/node_modules": true
        },
        "editor.folding": true
    }

## 4.2 Extensions

Visual Studio Code allows you to extend the built-in functionality with extensions.  To install the extensions press F1, type extension, select Install Extension and then type the name of the extension you want to install.

Below are the extensions that we will be using in this workshop.

**[Angular 1 Javascript and Typescript Snippets](https://marketplace.visualstudio.com/items?itemName=johnpapa.Angular1)**

Written by John Papa and follow his style guide.

    ng1controller // creates an Angular controller
    ng1directive  // creates an Angular directive
    ng1factory    // creates an Angular factory
    ng1module     // creates an Angular module
    ng1service    // creates an Angular service

**[Ionic v1 Snippets](https://marketplace.visualstudio.com/items?itemName=justinjames.ionic1-snippets)**

* Over 200 html/javascript snippets plus 700 ionicons.
* All snippets start with ionic
* All icons snippets start with ionicicon
* See [Full Docs](https://github.com/digitaldrummerj/vscode-ionic1-snippets/blob/master/docs.md) for usage

**[Cordova Tools](https://marketplace.visualstudio.com/items?itemName=vsmobile.cordova-tools)**

* Intellisense for ionic framework and core cordova plugins
* Includes a number of useful Javascript and HTML code Snippets for your project.  Just type ion_ in the editor to see what's available.

**More Snippets**

 See the [VSCode Market Place](https://marketplace.visualstudio.com/VSCode)


## Wrap-up

Now we are ready to start building our app.  The next lab we will create the master view of the master/detail pages and bind some data from a service to the UI.