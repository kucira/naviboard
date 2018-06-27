# naviboard JS

[![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/) 


Naviboard is a library for navigation with the help of keyboard/keypad in the feature phone web applications(e.g kaiOS applications). This library helps developer to think about logic rather than thinking about handling navigation in their web page by simple API's. Developers working on feature phones in new generation which need navigation support from keypad to browse in their native application will surely be benefited with this small javascipt library.It auto generates a schema based on desired navigation according to design.

Naviboard is available as a NPM module for use with node.js. If you don't use node to install the library then you can simply include naviboard.js or naviboard.min.js from the dist folder in this repo. These files are UMD wrapped so they can be used with or without a module loader such as requireJS.

```
 npm install naviboard
```

### Steps to setup: 
- After installing/including in `index.html` naviBoard will be available globally.Its ready to use like below:

Whenever the component(Angular, react etc) or the web page is initiating the loading, considering below as the first step:
Give class `navigable` to the elements which require navigation under a parent component.

```html
<div class="wrapper" id='ParentElementID'>
    <div class="box a navigable" tabindex="0">A</div>
    <div class="box b navigable" tabindex="0">B</div>
    <div class="box c navigable" tabindex="0">C</div>
    <div class="box d navigable" tabindex="0">D</div>
    <div class="box e navigable" tabindex="0">E</div>
</div>
```
Now give id as arguement to the API `setCurrentViewDOMNavigation` eg. ParentElementID in above case.

```javascript
 naviBoard.setCurrentViewDOMNavigation('ParentElementID')
```
Yippie!!
All set to navigate through the elements.But we are ignoring an important parameter to consider while doing this i.e `tabindex` . Don't forget to include this other wise you wont be able to navigate to the desired elements.

Now when we want to navigate other page or component, we need to destroy the previous component and set the new one for navigation. Its advisable to use destroy method associated with the component like `componentWillUnmount()` in react or `this.$onDestroy` in angular v1.6.

```javascript
 naviBoard.destroyCurrentViewDOMNavigation('ParentElementID')
```
### Other API's: 

When the client is getting refreshed we need to handle it by giving certain input to sustain our navigable items we use `refreshViewForNavigation` API.

e.g if a new component has been added in run time we need to update our library for taking care of the newly added element or removed element.

```javascript
 naviBoard.refreshViewForNavigation('ParentElementID',status)
```

status could be update ,destroy and refresh depending upon the change in navigation required in application.

-There is one more API for getting the current focused element by navigation. "By navigation" explicitly means that if focus is been hindered by other thing we might lose track of the desired navigation.

Current active element can be used to attach events. Like one can attach `click` event on element and can use `ng-click` on top of that.

```javascript
 naviBoard.getCurrentActiveElement()
```

Happy Coding!!!

> Use **naviboard** and suggest changes or modification required as its a small step for *developers* to save their time in order to navigate in feature phone applications instead writing lot of extra lines.