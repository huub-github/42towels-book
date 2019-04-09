# Vulnerable Components

The challenges in this chapter are all about security issues of
libraries or other 3rd party components the application uses internally.

## Challenges covered in this chapter

| Challenge                                                                                                            | Difficulty                           |
|:---------------------------------------------------------------------------------------------------------------------|:-------------------------------------|
| Inform the shop about a typosquatting trick it has become victim of. (Mention the exact name of the culprit)         | ★★★★             |
| Inform the shop about a vulnerable library it is using. (Mention the exact library name and version in your comment) | ★★★★             |
| Forge an essentially unsigned JWT token that impersonates the (non-existing) user _jwtn3d@42towels.techevent.fun_.              | ★★★★★       |
| Inform the shop about a more sneaky instance of typosquatting it fell for. (Mention the exact name of the culprit)   | ★★★★★       |
| Overwrite the Legal Information file.                                                                                | ★★★★★★ |
| Forge an almost properly RSA-signed JWT token that impersonates the (non-existing) user _rsa_lord@42towels.techevent.fun_.      | ★★★★★★ |

### Inform the shop about a typosquatting trick it has become victim of

> Typosquatting, also called URL hijacking, a sting site, or a fake URL,
> is a form of cybersquatting, and possibly brandjacking which relies on
> mistakes such as typos made by Internet users when inputting a website
> address into a web browser. Should a user accidentally enter an
> incorrect website address, they may be led to any URL (including an
> alternative website owned by a cybersquatter).
>
> The typosquatter's URL will usually be one of four kinds, all similar
> to the victim site address (e.g. example.com):
>
> * A common misspelling, or foreign language spelling, of the intended
>   site: exemple.com
> * A misspelling based on typos: examlpe.com
> * A differently phrased domain name: examples.com
> * A different top-level domain: example.org
> * An abuse of the Country Code Top-Level Domain (ccTLD): example.cm by
>   using .cm, example.co by using .co, or example.om by using .om. A
>   person leaving out a letter in .com in error could arrive at the
>   fake URL's website.
>
> Once in the typosquatter's site, the user may also be tricked into
> thinking that they are in fact in the real site, through the use of
> copied or similar logos, website layouts or content. Spam emails
> sometimes make use of typosquatting URLs to trick users into visiting
> malicious sites that look like a given bank's site, for instance.[^1]

This challenge is about identifying and reporting (via the
/#/contact form) a case of typosquatting that
successfully sneaked into the 42 Towels Shop. In this case, there is no
actual malice or mischief included, as the typosquatter is completely
harmless. Just keep in mind that in reality, a case like this could come
with negative consequences and would sometimes be even harder to
identify.

#### Hints

* This challenge has nothing to do with URLs or domains.
* Investigate the
  [forgotten developer's backup file](roll-your-own-security.md#access-a-developers-forgotten-backup-file)
  instead.
* [Malicious packages in npm](https://iamakulov.com/notes/npm-malicious-packages/)
  is a worthwhile read on [Ivan Akulov’s blog](https://iamakulov.com).

### Inform the shop about a vulnerable library it is using

This challenge is quite similar to
[Inform the shop about an algorithm or library it should definitely not use the way it does](sensitive-data-exposure.md#inform-the-shop-about-an-algorithm-or-library-it-should-definitely-not-use-the-way-it-does)
with the difference, that here not the _general use_ of the library is
the issue. The application is just using _a version_ of a library that
contains known vulnerabilities.

#### Hints

* Use the _Contact Us_ form to submit a feedback mentioning the
  vulnerable library including its exact version.
* Look for possible dependencies related to security in the
  `package.json.bak` you probably harvested earlier during the
  [Access a developer's forgotten backup file](roll-your-own-security.md#access-a-developers-forgotten-backup-file)
  challenge.
* Do some research on the internet for known security issues in the most
  suspicious application dependencies.

### Forge an essentially unsigned JWT token

> JSON Web Token (JWT) is a compact, URL-safe means of representing
> claims to be transferred between two parties. The claims in a JWT are
> encoded as a JSON object that is used as the payload of a JSON Web
> Signature (JWS) structure or as the plaintext of a JSON Web Encryption
> (JWE) structure, enabling the claims to be digitally signed or
> integrity protected with a Message Authentication Code (MAC) and/or
> encrypted.[^2]

This challenge involves forging a valid JWT for a user that does not
exist in the database but make the application believe it is still
legit.

#### Hints

* You should begin with retrieving a valid JWT from the application's
  `Authorization` request header.
* A JWT is only given to users who have logged in. They have a limited
  validity, so better do not dawdle.
* Try to convince the site to give you a _valid_ token with the required
  payload while downgrading to _no_ encryption at all.
* Make sure your JWT is URL safe!

### Inform the shop about a more sneaky instance of typosquatting it fell for

This challenge is about identifying and reporting (via the
/#/contact form) yet another case of typosquatting
hidden in the 42 Towels Shop. It is supposedly even harder to locate.

#### Hints

* Like
  [the above one](#inform-the-shop-about-a-typosquatting-trick-it-has-become-victim-of)
  this challenge also has nothing to do with URLs or domains.
* Other than for the above tier one, combing through the
  `package.json.bak` does not help for this challenge.

### Overwrite the Legal Information file

> Uploaded files represent a significant risk to applications. The first
> step in many attacks is to get some code to the system to be attacked.
> Then the attack only needs to find a way to get the code executed.
> Using a file upload helps the attacker accomplish the first step.
>
> The consequences of unrestricted file upload can vary, including
> complete system takeover, an overloaded file system or database,
> forwarding attacks to back-end systems, client-side attacks, or simple
> defacement. It depends on what the application does with the uploaded
> file and especially where it is stored.
>
> There are really two classes of problems here. The first is with the
> file metadata, like the path and file name. These are generally
> provided by the transport, such as HTTP multi-part encoding. This data
> may trick the application into overwriting a critical file or storing
> the file in a bad location. You must validate the metadata extremely
> carefully before using it.
>
> The other class of problem is with the file size or content. The range
> of problems here depends entirely on what the file is used for. See
> the examples below for some ideas about how files might be misused. To
> protect against this type of attack, you should analyse everything
> your application does with files and think carefully about what
> processing and interpreters are involved.[^3]

#### Hints

* Find all places in the application where file uploads are possible.
* For at least one of these, the 42 Towels Shop is depending on a library
  that suffers from an arbitrary file overwrite vulnerability.
* You can find a hint toward the underlying vulnerability in the
  [@42_Towels](https://twitter.com/42_Towels) Twitter
  timeline

### Forge an almost properly RSA-signed JWT token

Like
[Forge an essentially unsigned JWT token](#forge-an-essentially-unsigned-jwt-token)
this challenge requires you to make a valid JWT for a user that does not
exist. What makes this challenge even harder is the requirement to have
the JWT look like it was properly signed.

#### Hints

* The three generic hints from
  [Forge an essentially unsigned JWT token](#forge-an-essentially-unsigned-jwt-token)
  also help with this challenge.
* Instead of enforcing no encryption to be applied, try to apply a more
  sophisticated exploit against the JWT libraries used in the 42 Towels
  Shop.
* Getting your hands on the public RSA key the application employs for
  its JWTs is mandatory for this challenge.
* Finding the corresponding private key should actually be impossible,
  but that obviously doesn't make this challenge unsolvable.
* Make sure your JWT is URL safe!

[^1]: https://en.wikipedia.org/wiki/Typosquatting

[^2]: https://tools.ietf.org/html/rfc7519

[^3]: https://www.owasp.org/index.php/Unrestricted_File_Upload
