### Content

  1. [HTML Questions](#html-questions)
  1. [CSS Questions](#css-questions)
  1. [JS Questions](#js-questions)
  1. [Client Optimization](#client-optimization)
  1. [Network Questions](#network-questions)
  1. [Coding Questions](#coding-questions)
  1. [ OAuth 2.0](#oauth-2.0)
  1. [OOP](#oop)
  1. [PHP Secure](#php-secure)

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

<b>The Web Server Flow</b> sheme: https://github.com/aldb/not-to-step-on-a-rake/blob/master/img/webserverflow.jpg

<br>
<b>The Good Part</b>
<br>
OAuth 2.0 also provides several new grant types, which can be used to support many use-cases like native applications
<br>
<b>The Bad Parts</b>
* Different implementations and interact with them(separate pieces of code for Facebook, Google, Salesforce and etc)
* Short Lived Tokens: The spec does not mandate the lifetime and scope of the issued tokens. The implementation is free to have a token live forever. Although most of the implementations provide us with short-lived access tokens and a refresh token, which can be used to get a fresh access token.
* Security: The spec just "recommends" the use of SSL/TLS while sending the tokens in plaintext over the wire. Although, every major implementation has made it a requirement to have secure authorization endpoints as well require that the client must have a secure redirection URL

### OOP
 * Paradigm: Abstraction(Abstrcact Class) -> Encapsulation(can use method another class: $app->User()->getName(), where User in App class, getName in User class) -> Inheritance(class B extends A) -> Polymorphism(class Dog extends Animal implements Talk)
 <br>
 *  An <b>interface is a contract</b>: the guy writing the interface says, "hey, I accept things looking that way", and the guy using the interface says "Ok, the class I write looks that way".
 <br>
 An interface is an empty shell, there are only the signatures of the methods, which implies that the methods do not have a body. The interface can't do anything. It's just a pattern.
 <br>
Implementing an interface consumes very little CPU, because it's not a class, just a bunch of names, and therefore there is no expensive look-up to do. It's great when it matters such as in embedded devices.
  * <b>Abstract classes</b>, unlike interfaces, are classes. They are more expensive to use because there is a look-up to do when you inherit from them.

Abstract classes look a lot like interfaces, but they have something more : you can define a behavior for them. It's more about a guy saying, "these classes should look like that, and they have that in common, so fill in the blanks!".
  * Static classes work without new Object: $User::getName()

### PHP Secure

* Use SSL when authenticating users or performing sensitive operations.
* Regenerate the session id whenever the security level changes (such as logging in). You can even regenerate the session id every request if you wish.
* Manage a user session, using cookies (PHP does that for you) you can share some data between several HTTP requests, this is called a session. The user cookie will be used to load the server-side session storage, containing important data, such as Is my user an anonymous user or a connected one?. This is the Identification part.
* For additional protection against cookie theft through something like XSS, you might want to consider issuing unique cookies per IP address, and then making sure that the cookies are only useable from that IP address. If you're storing your cookies in the database, things can get complicated, as you now have multiple cookies mapping to the same user.
```
Set-Cookie: userName=Alice; salt=59843...; authCode=eeba9...
```
Where: authCode=HMAC(ROWID, userName + ipAddr + salt)
Salt value is generated randomly for every cookie you produce. There's no need to keep it a secret

Secure cookie settings:
```php
session_start();  
$currentCookieParams = session_get_cookie_params();  
$sidvalue = session_id();  
setcookie(  
    'PHPSESSID',//name  
    $sidvalue,//value  
    0,//expires at end of session  
    $currentCookieParams['path'],//path  
    $currentCookieParams['domain'],//domain  
    true, https only
    false, http only
);  
```
* Have sessions time out
* Don't use register globals
* Store authentication details on the server. That is, don't send details such as username in the cookie.
* Check the $_SERVER['HTTP_USER_AGENT']. This adds a small barrier to session hijacking. You can also check the IP address. But this causes problems for users that have changing IP address due to load balancing on multiple internet connections etc (which is the case in our environment here).
* Lock down access to the sessions on the file system or use custom session handling
* For sensitive operations consider requiring logged in users to provide their authenication details again
* Avoid XSS (keep your HTML well formed, take a look at PHPTAL or HTMLPurifier)
* <b>Cookie logic for remember me</b><br>
<b>Improved Persistent Login Cookie Best Practice</b>
<br>
You could use this strategy described here as best practice (2006) or an updated strategy described here (2015):
<br>
1) When the user successfully logs in with Remember Me checked, a login cookie is issued in addition to the standard session management cookie.
<br>
2) The login cookie contains a series identifier and a token. The series and token are unguessable random numbers from a suitably large space. Both are stored together in a database table, the token is hashed (sha256 is fine).
3)When a non-logged-in user visits the site and presents a login cookie, the series identifier is looked up in the database.
<br><br>
    3.1) If the series identifier is present and the hash of the token matches the hash for that series identifier, the user is considered authenticated. A new token is generated, a new hash for the token is stored over the old record, and a new login cookie is issued to the user (it's okay to re-use the series identifier).
<br>
    3.2) If the series is present but the token does not match, a theft is assumed. The user receives a strongly worded warning and all of the user's remembered sessions are deleted.
<br>
    3.3) If the username and series are not present, the login cookie is ignored.
 <br>   
This approach provides defense-in-depth. If someone manages to leak the database table, it does not give an attacker an open door for impersonating users.
