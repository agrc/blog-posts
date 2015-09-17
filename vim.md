# Boost Your Productivity With Vim
I was surprised to realize today that I have never written about one of my favorite tools that I use to write code. It's something that absolutely transformed my day-to-day coding. If it was suddenly taken away from me I would feel like I had gone back to the dark ages. That's right, I'm talk about Vim. Or more specifically Vim key bindings. <a href="https://en.wikipedia.org/wiki/Vim_(text_editor)">Vim (Vi IMproved)</a> is an old text editor that was first released in the 90's and is an improvement to an even older editor called Vi. The intriguing part of Vim for me was not the 20 year old piece of software but the system that it used to edit and navigate text. It's very efficient, requiring the coder to reach for his or her mouse almost never.

Lest you think that I've abandoned [my favorite text editor](https://atom.io/), the real power of Vim for me is not the actual software. In fact, I've only opened it up a few times out of curiosity. The power of Vim is the standard that it's set. There are Vim emulator plugins for every major text editor out there including [Sublime](https://github.com/guillermooo/Vintageous), [Atom](https://github.com/atom/vim-mode) and even [JSBin](https://jsbin.com/blog/my-zen-mode#vimmode). This means that if you invest the time into learning Vim commands they will be almost universally applicable across your development tools.

Want to quickly go to the end or beginning of the current line? Change everything within the quotes? Delete everything from your cursor to the end of the line? Quickly go to a line number? Change the casing of the selected text? This and [much, much, much](http://www.catswhocode.com/blog/130-essential-vim-commands) more can be done with just a few Vim commands.

Here are a few of the commands that convinced me that I should learn Vim:
 - `A` Go to the end of the line and start inserting new text.
 - `I` Same as `A` but go to the start of the line
 - `ci"` Delete everything within the quotes and start inserting new text
 - `C` Delete everything from the cursor to the end of the line and start inserting
 - `545 gg` Go to line number 545
 - `ct,` Delete everything until the "," and start inserting new text

These are just a few of the commands that I use every day. While it's significant learning curve, the time investment is worth it to me. After all...

<blockquote class="twitter-tweet" lang="en"><p lang="en" dir="ltr">Every year, the average Vim user saves over 4 seconds in accumulated time not having to reach for their mouse…</p>&mdash; I Am Devloper (@iamdevloper) <a href="https://twitter.com/iamdevloper/status/451792390865833984">April 3, 2014</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

There are endless tutorials available for you to learn Vim. After learning just a few of the basics I made it my practice to add one or two new commands to [my personal reference](https://www.evernote.com/l/ABdguLm6UtRExY8VU_EZWbfJvRKE6rpjTCM) on a regular basis. After a few weeks you'll wonder how you ever lived without it.

There are a few drawbacks that come to mind. Firstly, after a few months of using Vim, your fingers will start automatically typing commands into non-Vim interfaces. This can get annoying. Also, you've probably already realized that the learning curve is pretty steep. If you are not in a code editor on a daily basis then it's probably not worth the investment.

But if you're in the mood to boost your productivity and give your poor mouse a break you may want to play some [vim golf](http://www.vimgolf.com/) and see how it goes. :)
