# Sensitive Data Exposure

## Challenges covered in this chapter

| Challenge                                                                                                                                                                               | Difficulty                           |
|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------|
| Access a confidential document.                                                                                                                                                         | ★                               |
| Log in with MC SafeSearch's original user credentials without applying SQL Injection or any other bypass.                                                                               | ★★                         |
| Inform the shop about an algorithm or library it should definitely not use the way it does.                                                                                             | ★★                         |
| Log in with Amy's original user credentials. (This could take 93.83 billion trillion trillion centuries to brute force, but luckily she did not read the "One Important Final Note")    | ★★★                   |
| Gain access to any access log file of the server.                                                                                                                                       | ★★★★             |
| Identify an unsafe product that was removed from the shop and inform the shop which ingredients are dangerous.                                                                          | ★★★★             |
| (Not available) Dumpster dive the Internet for a leaked password and log in to the original user account it belongs to. (Creating a new account with the same password does not qualify as a solution.) | ★★★★★       |
| Perform an unwanted information disclosure by accessing data cross-domain.                                                                                                              | ★★★★★       |
| Forge a coupon code that gives you a discount of at least 80%.                                                                                                                          | ★★★★★★ |
| Solve challenge #999. Unfortunately, this challenge does not exist.                                                                                                                     | ★★★★★★ |
| Unlock Premium Challenge to access exclusive content.                                                                                                                                   | ★★★★★★ |

### Access a confidential document

Somewhere in the application you can find a file that contains sensitive
information about some - potentially hostile - takeovers the 42 Towels Shop
top management has planned.

#### Hints

* Analyze and tamper with links in the application that deliver a file
  directly.
* The file you are looking for is not protected in any way. Once you
  _found it_ you can also _access it_.

### Log in with MC SafeSearch's original user credentials

Another user login challenge where only the original password is
accepted as a solution. Employing SQL Injection or other attacks does
not count.

#### Hints

* MC SafeSearch is a rapper who produced the song
  ["Protect Ya' Passwordz"](https://www.youtube.com/watch?v=v59CX2DiX0Y)
  which explains password & sensitive data protection very nicely.
* After watching
  [the music video of this song](https://www.youtube.com/watch?v=v59CX2DiX0Y),
  you should agree that even ★★ is a slightly exaggerated
  difficulty rating for this challenge.

  [!["Protect Ya Passwordz"](img/protect-ya-passwordz.jpg)](https://www.youtube.com/watch?v=v59CX2DiX0Y)

### Inform the shop about an algorithm or library it should definitely not use the way it does

To fulfil this challenge you must identify a cryptographic algorithm (or
crypto library) that either
* should not be used _at all_
* or is a _bad choice_ for a given requirement
* or is used in an _insecure way_.

> Initially confined to the realms of academia and the military,
> cryptography has become ubiquitous thanks to the Internet. Common
> every day uses of cryptography include mobile phones, passwords, SSL,
> smart cards, and DVDs. Cryptography has permeated everyday life, and
> is heavily used by many web applications.
>
> Cryptography (or crypto) is one of the more advanced topics of
> information security, and one whose understanding requires the most
> schooling and experience. It is difficult to get right because there
> are many approaches to encryption, each with advantages and
> disadvantages that need to be thoroughly understood by web solution
> architects and developers. In addition, serious cryptography research
> is typically based in advanced mathematics and number theory,
> providing a serious barrier to entry.
>
> The proper and accurate implementation of cryptography is extremely
> critical to its efficacy. A small mistake in configuration or coding
> will result in removing a large degree of the protection it affords
> and rending the crypto implementation useless against serious attacks.
>
> A good understanding of crypto is required to be able to discern
> between solid products and snake oil. The inherent complexity of
> crypto makes it easy to fall for fantastic claims from vendors about
> their product. Typically, these are “a breakthrough in cryptography”
> or “unbreakable” or provide "military grade" security. If a vendor
> says "trust us, we have had experts look at this,” chances are they
> weren't experts![^1]

#### Hints

* Use the _Contact Us_ form to submit a feedback mentioning the abused
  algorithm or library.
* There are five possible answers and you only need to identify one to
  solve the challenge.
* Cryptographic functions only used in the
  [Apply some advanced cryptanalysis to find _the real_ easter egg](security-through-obscurity.md#apply-some-advanced-cryptanalysis-to-find-the-real-easter-egg)
  challenge _do not count_ as they are only a developer's prank and not
  a serious security problem.

### Log in with Amy's original user credentials

This challenge is similar to
[Log in with the administrators user credentials without previously changing them or applying SQL Injection](broken-authentication.md#log-in-with-the-administrators-user-credentials-without-previously-changing-them-or-applying-sql-injection)
in the sense that only using her original credentials will work as a
challenge solutions.

![Amy and Kif Kroker](img/amy_and_kif.jpg)

#### Hints

* As with so many other characters from
  [Futurama](http://www.imdb.com/title/tt0149460/) this challenge is of
  course about logging in as Amy from that show. In the picture above
  you see her together with her alien husband Kif.
* The challenge description contains a few sentences which give away
  some information how Amy decided to strengthen her password.
* Obviously, Amy - being a little dimwitted - did not put nearly enough
  effort and creativity into the password selection process.

### Gain access to any access log file of the server

> An access log is a list of all the requests for individual files that
> people have requested from a Web site. These files will include the
> HTML files and their imbedded graphic images and any other associated
> files that get transmitted. The access log (sometimes referred to as
> the "raw data") can be analyzed and summarized by another program.
>
> In general, an access log can be analyzed to tell you:
>
> The number of visitors (unique first-time requests) to a home page The
> origin of the visitors in terms of their associated server's domain
> name (for example, visitors from .edu, .com, and .gov sites and from
> the online services) How many requests for each page at the site,
> which can be presented with the pages with most requests listed first
> Usage patterns in terms of time of day, day of week, and seasonally
> Access log keepers and analyzers can be found as shareware on the Web
> or may come with a Web server.[^2]

The 42 Towels Shop application server is writing access logs, which can
contain interesting information that competitors might also be
interested in.

#### Hints

* Normally, server log files are written to disk on server side and are
  not accessible from the outside.
* Which raises the question: Who would want a server access log to be
  accessible through a web application?
* One particular file found in the folder you might already have found
  during the
  [Access a confidential document](#access-a-confidential-document)
  challenge might give you an idea who is interested in such a public
  exposure.
* Drilling down one level into the file system might not be sufficient.

### Identify an unsafe product that was removed from the shop and inform the shop which ingredients are dangerous

**TODO**

#### Hints

**TODO**

### Dumpster dive the Internet for a leaked password and log in to the original user account it belongs to

Not available

#### Hints

**TODO**

### Perform an unwanted information disclosure by accessing data cross-domain

Somewhere in the application there is an API endpoint which will allow
data to be accessed cross domain. Usually the same-origin policy would
prevent this but this endpoint has a special feature enabled which will
allow cross domain access under certain circumstances.

#### Hints

* Try to find and attack an endpoint that responds with user information. SQL Injection
  is not the solution here.
* What ways are there to access data from a web application cross-domain?
* This challenge uses an old way which is no longer recommended.

### Forge a coupon code that gives you a discount of at least 80%

This is probably one of the hardest challenges in the 42 Towels Shop.
As you learned during [the "happy path" tour](/part1/happy-path.md), the
web shop offers a _Coupon_ field to get a discount on your entire order
during checkout. The challenge is to get a discount of at least 80% on
an order. As no coupons with this high a discount are published, it is
up to you to forge your own.

#### Hints

* One viable solution would be to reverse-engineer how coupon codes are
  generated and craft your own 80% coupon by using the same (or at least
  similar) implementation.
* Another possible solution might be harvesting as many previous coupon
  as possible and look for patterns that might give you a leverage for a
  brute force attack.
* If all else fails, you could still try to blindly brute force the
  coupon code field before checkout.

### Solve challenge #999

The 42 Towels Shop is _so broken_ that even its convenience features
(which have nothing to do with the e-commerce use cases) are designed to
be vulnerable. One of these features is the
[automatic saving and restoring of hacking progress](/part1/challenges.md#automatic-saving-and-restoring-hacking-progress)
after a server crash or a few days pause.

In order to not mess with the _real challenges_ accidentally, the
challenge is to fake a signal to the application that you successfully
solved challenge #999 - which does not exist.

#### Hints

* Find out how saving and restoring progress is done behind the scenes
* Deduce from all available information (e.g. the `package.json.bak`)
  how the application encrypts and decrypts your hacking progress.
* Other than the user's passwords, the hacking progress involves an
  additional secret during its encryption.
* What would be a _really stupid_ mistake a developer might make when
  choosing such a secret?

### Unlock Premium Challenge to access exclusive content

These days a lot of seemingly free software comes with hidden or
follow-up costs to use it to its full potential. For example: In
computer games, letting players pay for _Downloadable Content_ (DLC)
after they purchased a full-price game, has become the norm. Often this
is okay, because the developers actually _added_ something worth the
costs to their game. But just as often gamers are supposed to pay for
_just unlocking_ features that were already part of the original
release.

This hacking challenge represents the latter kind of "premium" feature.
_It only exists to rip you hackers off!_ Of course you should never
tolerate such a business policy, let alone support it with your precious
Bitcoins!

That is why the actual challenge here is to unlock and solve the
"premium" challenge _bypassing the paywall_ in front of it.

#### Hints

* This challenge could also have been put into chapter
  [Weak security mechanisms](roll-your-own-security.md).
* There is no inappropriate, self-written or misconfigured cryptographic
  library to be exploited here.
* How much protection does a sturdy top-quality door lock add to your
  house if you...
  * ...put the key under the door mat?
  * ...hide the key in the nearby plant pot?
  * ...tape the key to the underside of the mailbox?
* Once more: **You do not have to pay anything to unlock this
  challenge!**

[^1]: https://www.owasp.org/index.php/Guide_to_Cryptography
[^2]: https://searchsecurity.techtarget.com/definition/access-log
