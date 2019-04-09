# Challenge tracking

## The Score Board

In order to motivate you to hunt for vulnerabilities, it makes sense to
give you at least an idea what challenges are available in the
application. Also you should know when you actually solved a challenge
successfully, so you can move on to another task. Both these cases are
covered by the application's score board.

On the score board you can view a list of all available challenges with
a brief description. Some descriptions are _very explicit_ hacking
instructions. Others are just _vague hints_ that leave it up to you to
find out what needs to be done.

![Partly solved Score Board](img/score-board_partly.png)

The challenges are rated with a difficulty level between ★ and
★★★★★★, with more stars representing a
higher difficulty. To make the list of challenges less daunting, they
are clustered by difficulty. By default only the 1-star challenges are
unfolded. You can open or collapse all challenge blocks as you like.
Collapsing a block has _no impact_ on whether you can _solve_ any of its
challenges.

The difficulty ratings have been continually adjusted over time based on
user feedback. The ratings allow you to manage your own hacking pace and
learning curve significantly. When you pick a 5- or 6-star challenge you
should _expect_ a real challenge and should be less frustrated if you
fail on it several times. On the other hand if hacking a 1- or 2-star
challenge takes very long, you might realize quickly that you are on a
wrong track with your chosen hacking approach.

Finally, each challenge states if it is currently _unsolved_ or
_solved_. The current overall progress is represented in a progress bar
on top of the score board. Especially in group hacking sessions this
allows for a bit of competition between the participants.

### Challenge Filters

Additional to the folding and unfolding of entire difficulty blocks, you
can filter the Score Board by [challenge categories](categories.md),
e.g. to focus on specific vulnerabilities. You can also hide all solved
challenges to reduce the level of distraction on the Score Board.

## Success notifications

The 42 Towels Shop employs a simple yet powerful gamification
mechanism: Instant success feedback! Whenever you solve a hacking
challenge, a notification is _immediately_ shown on the user interface.

!["Challenge solved!" push notification](img/challenge_solved_notification.png)

This feature makes it unnecessary to switch back and forth between the
screen you are attacking and the score board to verify if you succeeded.
Some challenges will force you to perform an attack outside of the 42 Towels
Shop web interface, e.g. by interacting with the REST API directly. In
these cases the success notification will light up when you come back to
the regular web UI the next time.

To make sure you do not miss any notifications they do not disappear
automatically after a timeout. You have to dismiss them explicitly. In
case a number of notifications "piled up" it is not necessary to dismiss
each one individually, as a simple reload of the UI in the browser (`F5`
key) will dismiss all at the same time.

Each challenge notification also shows a :checkered_flag: symbol with a character sequence next
to it. The code is relevant for participation in a CTF event.

The token should be entered in the main score system at [ctf.techevent.fun/challenges](https://ctf.techevent.fun/challenges)

## Automatic saving and restoring hacking progress

The _self-healing_ feature - by
wiping the entire database on server start - of the Shop was
advertised as a benefit just a few pages before. This feature comes at a
cost, though: As the challenges are also part of the database schema,
they will be wiped along with all the other data. This means, that after
every restart you start with a clean 0% score board and all challenges
in _unsolved_ state.

To keep the resilience against data corruption but allow users to _pick
up where they left off_ after a server restart, your hacking progress is
automatically saved whenever you solve a challenge - as long as you
allow Browser cookies!

After restarting the server, once you visit the application your hacking
progress is automatically restored:

![Auto-restoring hacking progress](img/autorestore-hacking-progress.png)

The auto-save mechanism keeps your progress for up to 30 days after your
previous hacking session. When the score board is restored to its prior
state, a torrent of success notifications will light up - depending on
how many challenges you solved up to that point. As mentioned earlier
these can be bulk-dismissed by reloading the page with the `F5` key.

If you want to start over with a fresh hacking session, simply click the
_Delete cookie to clear hacking progress_ button. After the next server
restart, your score board will be blank.
