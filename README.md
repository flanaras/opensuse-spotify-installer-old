# Spotify automatic installer for openSUSE

This script avoids the need to illegally redistribute Spotify binaries
by downloading the Linux client `.deb` from
[repository.spotify.com](http://repository.spotify.com/pool/non-free/s/spotify/),
converting it to `.rpm` format, and then installing it along with some
evil hacks to provide the necessary libraries where Spotify expects
them to be.

Currently only openSUSE 12.2 is supported.  Patches to support others
(e.g. [Factory](http://en.opensuse.org/Portal:Factory)) are very
welcome!

Credit and thanks for this installer go to:

* [Armin](http://community.spotify.com/t5/user/viewprofilepage/user-id/190504) on the Spotify community forums, who wrote the
[original version](http://community.spotify.com/t5/Desktop-Linux/Segfault-on-opensuse-12-2/m-p/161048/highlight/true#M1331).
* [Marguerite Su](https://github.com/marguerite) who provided an initial `.spec` file and helped eventually convince me it was worth moving away from `alien`.

Huge thanks also to the relatively anonymous Spotify employees such as
[parbo](http://community.spotify.com/t5/user/viewprofilepage/user-id/23361)
who have been donating some of their free time to make the Linux
client available.  *No* thanks go to Spotify middle/upper management
for consistently refusing to invest the small amount of resources
required to even acknowledge their Linux-based customers, let alone
support them.

## How to use

Shortly I am hoping to provide this installer conveniently
pre-packaged on [PackMan](http://packman.links2linux.org/).  Once you
have the `spotify-installer` rpm installed, installing Spotify is as
simple as running `install-spotify` as a non-root user.

In the mean time however, you can use it as follows:

1. Download the [`install-spotify.sh`](https://raw.github.com/aspiers/opensuse-spotify-installer/master/install-spotify.sh) script
2. Download [`spotify-client.spec`](https://raw.github.com/aspiers/opensuse-spotify-installer/master/spotify-client.spec) and place it in `/usr/src/packages/SPECS`
3. *(optional)* Read the source to make sure it's not going to [pwn](http://en.wikipedia.org/wiki/Pwn) your computer.
4. Make the script executable, e.g. from a terminal, type `chmod +x install-spotify.sh`
5. Run it as a non-root user, e.g. from a terminal type `./install-spotify.sh`

## License

This installer does *not* contain any material whatsoever copyrighted
by Spotify.

`install-spotify.sh` is a derivative of Armin's original version which
he posted it without any copyright notice, so I unless I hear
otherwise I'll assume it's in the public domain.

`spotify.spec` is a derivative of Marguerite Su's original version,
and the header seems to imply that it's MIT-licensed (since the
pristine package the header refers to is either Spotify or
non-existent, depending on how you look at it).

Therefore I think it's fair to say the overall license is MIT (i.e.
less ambiguously, the X11 license).

## Support, bugs, development etc.

Please check the [issue tracker](https://github.com/aspiers/opensuse-spotify-installer/issues)
for known issues, and if yours is not there, please submit it.
I can't guarantee that I'll be able to fix it, or even respond,
but I'll try, and even if I can't help, this is github, so anyone else
can potentially help you out too.

Even better, if you know how to fix a problem with the script, please
[fork this repository](https://github.com/aspiers/opensuse-spotify-installer/fork_select), commit
your fix, and then send me a [pull request](https://help.github.com/articles/using-pull-requests)!

## Why not just use the new web-based player?

There's a new browser-based Spotify player accessible via
https://play.spotify.com/ or https://apps.facebook.com/get-spotify/

However, [it does not seem to be generally available yet](http://howto.cnet.com/8301-11310_39-57551372-285/enable-spotifys-web-player-right-now/), and [is missing many features](http://community.spotify.com/t5/Desktop-Linux/ANNOUNCE-Spotify-0-8-4-for-GNU-Linux/m-p/204364/highlight/true#M1687) compared to the standalone Linux client.

## Why is this script here on github?

I hope it's kind of obvious from the above.  But since you
got me on the soapbox ...

`<rant length="very long">`

Web forums breed endless technological misery.  They are bloated,
slow, clunky quagmires which result in long meandering threads of
unstructured communication.  Trying to install Spotify after every
distribution upgrade typically involves the following steps:

1. google for something like 'spotify opensuse 12.2'
2. wade through a *huge* number of hits from web forum threads or blog post or wiki page,
   many of which are too old to be useful
3. select the most promising looking hit
4. wade through a long forum thread or web page
5. re-live other people's trial-and-error experiences
6. realise that most people on this thread don't really know what they're doing
   and no-one fully figured it out
7. repeat steps 3--6 a few times
8. observe that every man and his dog has come up with their own
   partial solution which is similar but slightly different to the next
   person's, due to various gotchas which apply in some cases but not others
9. scream "I don't care, I just want the ****ing thing to work!" a few times
10. mentally recombine several different nuggets of information
11. experiment a bit

... and eventually maybe you get it to work.  If you're really lucky
Spotify might only segfault occasionally!

(If I was [rms](http://en.wikipedia.org/wiki/Richard_Stallman), now
would be the time to point out that this is inevitable karma for
trying to use [freedom-denying software](http://www.gnu.org/philosophy/);
sadly I do not possess as much integrity as him though.)

I've been working closely with Linux since 1995 and even with a lot of
experience I find process this painful and frustrating every time.  So
I can't imagine how annoyed Linux newbies must get when they want to
do something as conceptually simple as installing Spotify on an
rpm-based distro, and find that they have to struggle through this
crap.  It flies against *all* conventional wisdom regarding best
practices in software development and deployment.

Going through this yet again after this latest upgrade to openSUSE
12.2 was the straw that broke the camel's back (Fedora 16 was the
penultimate straw...)  So let's take a stand.  We can and will do
better!  Barring an unexpected miracle from Spotify management where
they suddenly decide to stop ignoring their Linux user base, the
solution is relatively simple.  We just need to treat the problem with
respect, i.e. just like any other free or open source software project
out there - it deserves standard best practices.  That means an
automated deployment mechanism which is tracked properly using
decentralized version control, a bug tracker, and a collaborative
platform which allows anyone to chip in and help in a *structured*
fashion.  Fortunately github is totally mind-bendingly awesome at
this, and free!  So let's use it!

`</rant>`
