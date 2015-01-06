<!-- 
.. title: Trying out Fish Shell
.. slug: trying-out-fish-shell
.. date: 2015-01-06 07:44:51 UTC-08:00
.. tags: shell,fish
.. link: 
.. description: 
.. type: text
-->

I changed my current shell in stjerm and lilyterm to fish a few months ago. I 
can't believe why I wasn't using this before since it's like having kupfer on
the commandline in terms of ease of use. Of course, I had to port my aliases
and some of my functions over to fish, but that was pretty easy to do.

# Resources
* [Where I found out about using expr from coreutils to fill in for missing string manip functionality](https://github.com/fish-shell/fish-shell/issues/924)
* [In case you need multiline text literally in env vars](https://github.com/fish-shell/fish-shell/issues/159)
* Confused on how to split strings into arrays? Just try this: ```count (echo 0:0:0|sed 's/:/\n/g')```
* And of course, my [dotfiles](https://github.com/shadowkyogre/dotfiles)
