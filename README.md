# Luke's Auto-Rice Bootstraping Scripts (LARBS) - Void Edition

## A fork of LARBS?

Technically, yes, but basically the same.

Since the [launch of LARBS 1.0](https://www.youtube.com/watch?v=yo1qqUH6_O4), I've grown accustomed to using the efficient keybinds, scripts, and programs despite it becoming a [big meme](https://i.imgur.com/WhnDjww.jpg).

LARBS Void Edition, as the name implies, is optimized to work exclusively on Void Linux with dwm. I wanted to bring it back to just one set of keybinds, programs, and scripts that are clear and easy to wrap your head around.

LARBS Void Edition allows you to skip the relatively demanding task of building a custom Void Linux system. You get a complete foundation that can be up and running within 10 minutes while remaining minimal, efficient, and modular.

The goal is to keep it light weight, fast, and reasonably unchanging (aside from your personal customizations) so that you don't have to worry about constantly swapping out programs or fixing broken scripts in the future.

## Who's it for?

It's designed for people who aren't afraid of poking around in config files and reading man pages. It's great for people who want a customizable system without spending hours or days building one from scratch.

The command line is the main interface in LARBS. Therefore, it's intended for people who are comfortable writing/modifying shell scripts and config files.

_If your workflow requires specific programs or hardware devices, you may want to avoid installing LARBS Void Edition on your main machine. You may run into trouble with devices such as printers, bluetooth, or wifi. Some devices may require manual setup to get working_

If it's important that your system runs clean and efficiently, free from reliance on ~~bloated~~ "fully featured" programs, then LARBS Void Edition might be exactly what you're looking for.

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

__Note: some of the scripts that LARBS deploys assume that certain programs are installed, so be sure to install necessary dependencies if you're going to use your own package list.__

### The `progs.csv` list

LARBS will parse the given programs list and install all given programs. Note
that the programs file must be a three column `.csv`.

The first column is a "tag" that determines how the program is installed, ""
(blank) for the main repository or `G` if the program is a
git repository that is meant to be `make && sudo make install`ed.

The second column is the name of the program in the repository, or the link to
the git repository, and the third comment is a brief description.

Depending on your own build, you may want to tactically order the programs in
your programs file. LARBS will install the programs in order from top to bottom.

__If you include commas in your program descriptions, be sure to include double quotes around the whole description to ensure correct parsing.__

### The script itself

The script is broken up extensively into functions for easier readability and
trouble-shooting. Everything should be self-explanatory.

The main work is done by the `installationloop` function, which iterates
through the programs file and determines based on the tag of each program,
which commands to run to install it.

## Post Installation Recommendations

To receive the latest updates to `voidrice`, you could simply pull them down using git, however this can conflict with any changes you've made locally.

Some knowledge of `git` is recommended, but to make things easier, some of the commonly customized files have been isolated.

For example, you can place all of your personal directories and files in `~/.config/directories` or `~/.config/files` and the `shortcuts` script will take care of applying those changes to zsh and the lf file manager.

Additionally, `~/.config/aliasrc` is for adding your personal aliases and zsh commands.

To be clear, *The aliasrc, files, and directories files will not receive future updates* so they are safe to modify as much as you like.

However, if you modify files like `~/.config/nvim/init.vim` or `~/.config/zsh/.zshrc`, you may want to consider backing up your changes. I usually just generate a diff file for this.

Personally, I put all additional packages and configs that are personal to my workflow in a separate shell script that I run after the main LARBS setup.

This separation keeps LARBS clean and easy to understand.

It's purposefully simple, but if you have ideas on how to make it more elegant, feel free to submit a pull request or contact me:

am@claridge.xyz
