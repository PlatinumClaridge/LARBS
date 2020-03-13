# Luke's Auto-Rice Bootstraping Scripts (LARBS) - Void Edition

## A fork of LARBS?

Technically, yes, but basically the same.

Since the [launch of LARBS 1.0](https://www.youtube.com/watch?v=yo1qqUH6_O4), I've grown accustomed to using the efficient keybinds, scripts, and programs despite it becoming a [big meme](https://i.imgur.com/WhnDjww.jpg).

LARBS Void Edition, as the name implies, is optimized to work exclusively on Void Linux with dwm. I wanted to bring it back to just one set of keybinds, programs, and scripts that are clear and easy to wrap your head around. I've also removed a number of scripts and commands that were personalized to Luke's work flow.

LARBS Void Edition allows you to skip the relatively demanding task of building a custom Void Linux system. You get a complete foundation that can be up and running within 10 minutes while remaining minimal, efficient, and modular.

The goal is to keep it light weight, fast, and reasonably unchanging (aside from your personal customizations) so that you don't have to worry about constantly swapping out programs or fixing broken scripts in the future.

## Who's it for?

It's designed to be an excellent starting point for people who aren't afraid of poking around in config files and reading man pages. It's great for people who want a customizable system without spending hours or days building one from scratch.

If you're interested in teaching yourself the Linux ropes, LARBS provides an easy window into learning the command line, writing/modifying shell scripts, and how Linux works as a whole.

_If your workflow requires specific programs or hardware devices, you may want to avoid installing LARBS Void Edition on your main machine. You may run into trouble with devices such as printers, bluetooth, or wifi. Some devices may require manual setup to get working_

## Installation:

On a Void based distribution as root, run `xbps-install -Su` to assure your system is up to date, then run the following:

```
xbps-install wget
wget https://claridge.xyz/larbs.sh
sh larbs.sh
```

That's it.

## What is LARBS?

LARBS is a script that autoinstalls and autoconfigures a fully-functioning
and minimal terminal-and-vim-based Void Linux environment.

LARBS is intended to be run on a fresh install of Void Linux, and
provides you with a fully configured diving-board for work or more
customization.

## Customization

By default, LARBS uses the programs [here in progs.csv](progs.csv) and installs
[the voidrice dotfiles here](https://github.com/PlatinumClaridge/voidrice),
but you can easily change this by either modifying the default variables at the
beginning of the script or giving the script one of these options:

- `-r`: custom dotfiles repository (URL)
- `-p`: custom programs list/dependencies (local file or URL)

### The `progs.csv` list

LARBS will parse the given programs list and install all given programs. Note
that the programs file must be a three column `.csv`.

The first column is a "tag" that determines how the program is installed, ""
(blank) for the main repository or `G` if the program is a
git repository that is meant to be `make && sudo make install`ed.

The second column is the name of the program in the repository, or the link to
the git repository, and the third comment is a description (should be a verb
phrase) that describes the program. During installation, LARBS will print out
this information in a grammatical sentence. It also doubles as documentation
for people who read the csv or who want to install the voidrice dotfiles manually.

Depending on your own build, you may want to tactically order the programs in
your programs file. LARBS will install the programs in order from top to bottom.

If you include commas in your program descriptions, be sure to include double quotes around the whole description to ensure correct parsing.

### The script itself

The script is broken up extensively into functions for easier readability and
trouble-shooting. Everything should be self-explanatory.

The main work is done by the `installationloop` function, which iterates
through the programs file and determines based on the tag of each program,
which commands to run to install it. You can easily add new methods of
installations and tags as well.

It's purposefully a very simple script, but if you have ideas on how to make it more elegant, feel free to submit a pull request or contact me:

am@claridge.xyz
