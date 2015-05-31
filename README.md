### Content

  1. [HTML Questions](#html-questions)
  1. [CSS Questions](#css-questions)
  1. [JS Questions](#js-questions)
  1. [Client Optimization](#client-optimization)
  1. [Network Questions](#network-questions)
  1. [Coding Questions](#coding-questions)

#### HTML Questions: 
  * What does a doctype do?
  
      The doctype declaration should be the very first thing in an HTML document, before the tag. The doctype      declaration is not an HTML tag; it is an instruction to the web browser about what version of the markup language the page is written in. The doctype declaration refers to a Document Type Definition (DTD).
  
  * What's the difference between HTML and XHTML?
  
  HTML5 has two parsing modes or syntaxes: HTML and XML. The difference depends on whether the document is served with a Content-type: text/html header or a Content-type: application/xml+xhtml header. [More info](http://www.sitepoint.com/web-foundations/differences-html-xhtml/)

  * Describe the difference between a cookie, sessionStorage and localStorage
  
  In terms of capabilities, cookies only allow you to store strings. sessionStorage and localStorage allow you to store JavaScript primitives but not Objects or Arrays (it is possible to JSON serialise them to store them using the APIs). Session storage will generally allow you to store any primitives or objects supported by your Server Side language/framework. [More](http://stackoverflow.com/questions/19867599/what-is-the-difference-between-localstorage-sessionstorage-session-and-cookie)
  
### CSS Questions
  * How added tag Vertical Alignment?
    ```css
      display: table-cell;
      vertical-align: middle;
    ```

### JS Questions
  * What's the difference between a variable that is: null, undefined or undeclared?
```javascript
typeof null //'object';
typeof undeclared //'undefined';
typeof undefined //'undefined';
```
  * How dublicate arr?
```javascript
arr.concat(arr);
//or
arr.push.apply(arr,arr);
```

### Client Optimization

  * Images: Used css sprite, .PNG. Not change image size(width, height), create original images if need. Make favicon.ico Small and Cacheable.
  * Union load JS files in one file(also css)
  * Put CSS files in header
  * Put JS files in bottom page
  * Minify CSS and JS files
  * Used subdomes for load your content(IMG, video and etc). For HTTP/ 1.1 you can at the same time load content from one host.
  * Used cache - Add an Expires or a Cache-Control Header. Make Ajax Cacheable. 
  * Avoid CSS Expressions, Redirects, Duplicate Scripts
  * Reduce Cookie Size
