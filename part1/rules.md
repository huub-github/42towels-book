# Hacking exercise rules

## ✔ Recommended hacking tools

### Browser

When hacking a web application a good internet browser is mandatory. The
emphasis lies on _good_ here, so you do _not_ want to use Internet
Explorer. Other than that it is up to your personal preference. Chrome
and Firefox both work fine from the authors experience.

#### Browser development toolkits

When choosing a browser to work with you want to pick one with good
integrated (or pluggable) developer tooling. Google Chrome and Mozilla
Firefox both come with powerful built-in _DevTools_ which you can open
via the `F12`-key.

When hacking a web application that relies heavily on JavaScript, **it
is essential to your success to monitor the _JavaScript Console_
permanently!** It might leak valuable information to you through error
or debugging logs!

![DevTools Console tab](img/devtools_console.png)

Other useful features of browser DevTools are their network overview as
well as insight into the client-side JavaScript code, cookies and other
local storage being used by the application.

![DevTools Network tab](img/devtools_network.png)

![DevTools Sources tab](img/devtools_sources.png)

![DevTools Application tab](img/devtools_cookies.png)

#### Tools for HTTP request tampering

On the _Network_ tab of Firefox's DevTools you have the option to _Edit
and Resend_ every recorded HTTP request. This is extremely useful when
probing for holes in the server-side validation logic.

This can also be helpful when trying to bypass certain input validation
or access restriction mechanisms, that are not properly checked _on the
server_ once more.

An API testing plugin like
PostMan (see Managed Software Center for availability)
 allows you to communicate with the RESTful backend of a web
application directly. Skipping the UI can often be useful to circumvent
client-side security mechanisms or simply get certain tasks done faster.
Here you can create requests for all available HTTP verbs (`GET`,
`POST`, `PUT`, `DELETE` etc.) with all kinds of content-types, request
headers etc.

If you feel more at home on the command line, `curl` will do the trick
just as fine as the recommended browser plugins.

#### Scripting tools

A small number of challenges is not realistically solvable manually
unless you are cheating or are incredibly :four_leaf_clover:-lucky.

For these challenges you will require to write some scripts that for
example can submit requests with different parameter values
automatically in a short time. As long as the tool or language of choice
can submit HTTP requests, you should be fine. Use whatever you are most
familiar with.

If you have little experience in programming, best pick a language that
is easy to get into and will give you results without forcing you to
learn a lot of syntax elements or write much _boilerplate code_. Python,
or JavaScript give you this simplicity and ease-of-use. If you
consider yourself a "command-line hero", Bash will get the
job done for you. Languages like Java, C# or Perl are probably less
suitable for beginners. In the end it depends entirely on your
preferences, but being familiar with at least one programming language
is kind of mandatory if you want to get 100% on the score board.

> In computer programming, boilerplate code or boilerplate refers to
> sections of code that have to be included in many places with little
> or no alteration. It is often used when referring to languages that
> are considered verbose, i.e. the programmer must write a lot of code
> to do minimal jobs.[^1]

### Penetration testing tools

You _can_ solve all challenges just using a browser and the
plugins/tools mentioned above. 

This is also the _recommended_ set of tools to start with. 

Please contact the security team for any product that you'd like to use.

#### Burp Suite

Burp suite might be available in Managed Software Center for you depending on your department. Go to [their documentation to get started](https://portswigger.net/burp/documentation/desktop/getting-started).
 

**Note** that running a full scan is not allowed for this CTF event. You can however replicate requests and script or iterate requests.

### Internet

You are free to use Google during your hacking session to find helpful
websites or tools. The 42 Towels Shop is leaking useful information
all over the place if you know where to look, but sometimes you simply
need to extend your research to the Internet in order to gain some
relevant piece of intel to beat a challenge.

Do realize that once you start searching for the answers/solutions you will find the answer, _this is considered cheating_.

## :bulb: Getting hints

Frankly speaking, you are reading the _premium source of hints_ right
now! Congratulations! In case you want to hack more on your own than
[follow the breadcrumbs through the wood of challenges in part II](../part2/README.md),
the most direct way to ask for specific hints for a particular challenge
is the chat.

Note that the individual challenges at [ctf.techevent.fun](https://ctf.techevent.fun) contain very specific hints for each challenge.

## :x: Things considered cheating

### Reading a solution ( :godmode: ) before trying

The Part II and the internet is
there to help you in case you are stuck or have absolutely no idea how a
specific challenge is solved. 

You have been warned.

### Source code

42 Towels Shop is supposed to be attacked in a "black box" manner. That
means you cannot look into the source code to search for
vulnerabilities. As the application tracks your successful attacks on
its challenges, the code must contain checks to verify if you succeeded.
These checks would give many solutions away immediately.

The same goes for several other implementation details, where
vulnerabilities were arbitrarily programmed into the application. These
would be obvious when the source code is reviewed.

Finally the end-to-end test suite of 42 Towels Shop was built hack all
challenges automatically, in order to verify they can all be solved.
These tests deliver all the required attacks on a silver plate when
reviewed.

### GitHub repository

While stated earlier that "the Internet" is fine as a helpful resource,
consider GitHub repositories
as entirely off limits. First and foremost because it contains the
source code (see above).

### Database table `Challenges`

The challenges (and their progress) live in one database together with
the rest of the application data, namely in the `Challenges` table. Of
course you could "cheat" by simply editing the state of each challenge
from _unsolved_ to _solved_ by setting the corresponding `solved` column
to `1`. You then just have to keep your fingers crossed, that nobody
ever asks you to _demonstrate how_ you actually solved all the 4- and
5-star challenges so quickly.

### Configuration REST API Endpoint

The 42 Towels Shop offers a URL to retrieve configuration information which
is required by the [Customization](customization.md) feature that allows
redressing the UI and overwriting the product catalog:
`/rest/admin/application-configuration`

The returned JSON contains spoilers for all challenges that depend on a
product from the inventory which might be customized. As not all
customization can be prepared on the server side, exposing this REST
endpoint is unavoidable for some
features to work properly.

### Score Board HTML/CSS

The Score Board and its features were covered in the
[Challenge tracking](challenges.md) chapter. In the current context of
"things you should not use" suffice it to say, that you could manipulate
the score board in the web browser to make challenges _appear as
solved_. Please be aware that this "cheat" is even easier (and more
embarrassing) to uncover in a classroom training than the previously
mentioned database manipulation: A simple reload of the score board URL
will let all your local CSS changes vanish in a blink and reveal your
_real_ hacking progress.

[^1]: https://en.wikipedia.org/wiki/Boilerplate_code


