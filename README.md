### Content

  1. [HTML Questions](#html-questions)
  1. [CSS Questions](#css-questions)
  1. [JS Questions](#js-questions)
  1. [Client Optimization](#client-optimization)
  1. [Network Questions](#network-questions)
  1. [Coding Questions](#coding-questions)
  1. [ OAuth 2.0](#oauth-2.0)

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

### Coding Questions

  *Is palindrome
```javascript
function is_palindrome(str) {
  str = str.replace(/[^a-zA-Z ]/g, ""); //Del all special charcaters
  if(str[0] !== str[str.length-1]) return false; //Check for long string
  return str === str.split('').reverse().join('');
}
```
### OAuth 2.0
OAuth is often described as a valet key for the web.
Sense: can get access from you social network, withou info about your friends, calendar and etc.
<br>
<b>Various OAuth Flows</b>
<ul>
<li> <b> User-Agent Flow </b> : Suitable for clients typically implemented in user-agents (for example, clients running inside a web browser) using a scripting language such as JavaScript. Mostly used by native applications for mobile or desktop, leveraging the embedded or external browser as the user-agent for authorization and it uses the <i>Implicit Grant</i> authorization.</li>
<li> <b> Web Server Flow </b> : This makes use of the <i>Authorization Code</i> grant and is a redirection-based flow which requires interaction with the end-user's user-agent. Thus, it is most suitable for clients which are a part of web-server based applications, that are typically accessed via a web browser. </li>
<li> <b> Username and Password Flow </b> :  Used only when there is a high trust between the client and the resource owner and when other flows are not viable, as it involves the transfer of the resource owner's credentials. Examples of clients can be a device operating system or a highly privileged application. This can also be used to migrate existing clients using HTTP Basic or Digest Authentication schemes to OAuth by converting the stored credentials to an access token. </li>
<li> <b> Assertion Flow </b> : Your client can present an assertion such as SAML Assertion to the authorization server in exchange for an access token. </li>
<li> <b> Client Credentials Flow </b> : OAuth is mainly used for delegated access, but there are cases when the client owns the resource or already has been granted the delegated access outside of a typical OAuth flow. Here you just exchange client credentials for an access token. </li>
</ul>

<b>The Web Server Flow</b> sheme: </img src="https://github.com/aldb/not-to-step-on-a-rake/blob/master/img/webserverflow.jpg?raw=true">

<br>
<b>The Good Part</b>
OAuth 2.0 also provides several new grant types, which can be used to support many use-cases like native applications
<b>The Bad Parts</b>
* Different implementations and interact with them(separate pieces of code for Facebook, Google, Salesforce and etc)
* Short Lived Tokens: The spec does not mandate the lifetime and scope of the issued tokens. The implementation is free to have a token live forever. Although most of the implementations provide us with short-lived access tokens and a refresh token, which can be used to get a fresh access token.
* Security: The spec just "recommends" the use of SSL/TLS while sending the tokens in plaintext over the wire. Although, every major implementation has made it a requirement to have secure authorization endpoints as well require that the client must have a secure redirection URL
