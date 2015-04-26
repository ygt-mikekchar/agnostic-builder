# Agnostic Builder

Note: This is a fork of https://github.com/chriskempson/base16-builder
      This has saved me quite a bit of time and I'd like to thank Chris
      for making it.  As much as possible, I hope to track the
      upstream code and not add much of my own code.

Easily build color palettes of Agnostic with YAML scheme definitions
and ERB templates.  It will generate output that can be used to
install the palettes for different terminal environments
See the [Agnostic](https://github.com/ygt-mikekchar/agnostic) repository
for more information about Agnostic.

Requires Ruby 1.9 or greater.

## Usage
    > ./build-agnostic
Build all schemes

    > ./build-agnostic -s schemes/default.yml
Build only the "default" theme

    > ./build-agnostic https://awesome-schemes.com/my-scheme.yml
Build a scheme stored on some webspace.

## How does it work?

A "scheme" is a yml YAML file that defines a 16 colour palette
of colours.  The palette can be used to determine which colour
corresponds with which colour number when used with the Agnostic
colorscheme.  Depending on your mood, or the environment you are
working in, you might want to change the colors in the palette
while still using the same colorscheme for this reason there
are many "schemes" in the scheme directory.

Knowing which colour corresponds with which colour number
is not quite enough, though.  You also need to configure your
terminal emulator to use those colours.  build-agnostic
is a script that uses a template to build configuration files
for various terminal emulators (often as a shell script that
you can run).  The details of how to output the configuration
file is stored in a "template" in the templates directory.

## Differences from Base16-Builder

Agnostic has slightly different goals than Base16.  Agnostic is
meant to be used a 16 colour colorscheme that supports many
different colour palettes in a shared terminal session.  For
that reason many of the templates don't really apply to Agnostic
and have been removed.  Unfortunately, Base16 makes some
different colour assumptions that probably won't work
with the Agnostic colorscheme, so there is no point in keeping
the original Base16 schemes.  For that reason, only Agnostic
compatible schemes are in the schemes directory.

### Working with upstream

Our goal here is to modify Base16-Builder as little as possible.
This means that there will be times when you will want to
merge in code from the upstream branch.  I recommend adding
the following git remote:

```
git remote add upstream https://github.com/chriskempson/base16-builder.git
```

Every once in a while to a `git fetch upstream` to keep the
upstream version up to date.  Some examples:

Merge upstream changes:
```
git merge upstream/master
```

Checkout a template that is not in Agnotic-Builder yet:
```
git checkout upstream/master -- templates/template-name
```

Don't ever push to upstream :-)

## Templates

After much consideration (at least 20 seconds), I have
decided that the easiest route will be to remove *all*
of the original templates and then add them back one
at a time as they are needed.  If you wish to have one
of the original templates supported, then just check
it out the base16-builder repository, modify it and
add it back to agnostic builder.

### Currently Supported Templates

* xresources

## Original Base16-Builder Maintainers
* [chriskempson](https://github.com/chriskempson) - HTML Preview, Vim, TextMate, iTerm 2, XFCE4 Terminal, Mou, Escape Code Shell Script, Gnome Terminal, BBEdit
* [jayferd](https://github.com/jayferd) - Rouge
* [neil477](https://github.com/neil477) - Emacs
* [joedynamite](https://github.com/joedynamite) - Xcode 4
* [robloach](https://github.com/robloach) - Geany
* [geoffstokes](https://github.com/geoffstokes) - Windows Command Prompt, MinTTY
* [idleberg](https://github.com/idleberg) - Atom, Chrome DevTools, CodeMirror, Gedit, highlight.js, Notepad++, prettify.js, Pygments, Rainbow
* [rgieseke](https://github.com/rgieseke) - Textadept
* [oxplot](https://github.com/oxplot) - Mate Terminal
* [esn89](https://github.com/esn89) - Zathura PDF Reader
* [romainx](https://github.com/romainx) - MultiMarkdown Composer 2
* [moonpyk](https://github.com/moonpyk) - ConEmu
* [jprjr](https://github.com/jprjr) - ConnectBot, vx-connectbot

## License

Generally speaking we won't modify the executable code in this project, so
the copyright belongs to the original authors.  We will also maintain the
original license (MIT).  The scheme files are not copyrightable as they are
simply descriptions of 16 colour combinations.  Apart from the agnostic
specific colour palettes the schemes were derived from public sources
of information.

Base16 Builder is released under the
[MIT License](https://github.com/chriskempson/base16-builder/blob/master/LICENSE.md)
