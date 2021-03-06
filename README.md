# Dominion Divider Generation

[![Join the chat at https://gitter.im/dominiontabs/Lobby](https://badges.gitter.im/dominiontabs/Lobby.svg)](https://gitter.im/dominiontabs/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

## Introduction

This is a script and library to generate card dividers for storing cards for the game [Dominion](https://boardgamegeek.com/boardgame/36218/dominion). If you are just looking go generate some dominion dividers, there is no need to install this script as I host a [live version of this generator code](http://domtabs.sandflea.org). However, if you want to use arguments that I don't expose on that page, or change the code, or contribute to the project the full generation code (not the web interface or the fonts) is included here, and contributions are more than welcome.

Again, to generate tabs go to the ***[Online Generator](http://domtabs.sandflea.org)***.

## Prerequisites

#### Python Packages
You need the python packages for reportlab (http://www.reportlab.com/software/opensource/rl-toolkit/download/) and PIL (http://www.pythonware.com/products/pil/) installed. You can install them manually or use the included setup.py via 'python setup.py install' (perhaps run via 'sudo' if not in a virtual env) which should install everything for you.

#### Fonts
I believe I cannot distribute one font (Minion Pro) domdiv uses as they are owned by Adobe with a License that I understand to disallow redistribution.

However, it appears you can download them here:
- http://fontsgeek.com/fonts/Minion-Pro-Regular
- http://fontsgeek.com/fonts/Minion-Pro-Italic
- http://fontsgeek.com/fonts/Minion-Pro-Bold

Alternatively, the font files are included with every install of the free Adobe Reader. For example, on Windows 7 they are in C:\Program Files (x86)\Adobe\Reader 9.0\Resource\Font called `MinionPro-Regular.otf`, `MinionPro-Bold.otf` and `MinionPro-It.otf`. 

Sadly, all these fonts use features that are not support by the reportlab package. Thus, they need to first be converted to ttf (TrueType) format. I used the open source package fontforge to do the conversion. Included as 'convert.ff' is a script for fontforge to do the conversion, on Mac OS X with fontforge installed through macports or homebrew you can just run `./convert.ff MinionPro-Regular.otf`, `./convert.ff MinionPro-Bold.otf` and `./convert.ff MinionPro-It.otf`. With other fontforge installations, you'll need to change the first line of convert.ff to point to your fontforge executable. I have not done this step under Windows - I imagine it may be possible with a cygwin install of fontforge or some such method. 

Copy the converted `.ttf` files to the `fonts` directory in the `domdiv` package/directory, then perform the package install below.

## Install/Running
Run `python setup.py install`. This should install the needed prerequisites and make a script called `dominion_dividers` available in your python script directory. Run `dominion_dividers <outfile>` to get a pdf of all dividers with the default options, or run `dominion_dividers --help` to see the (extensive) list of options.

## Using as a library
The library will be installed as `domdiv` with the main entry point being `domdiv.main.generate(options)`. It takes a `Namespace` of options as generated by python's `argparser` module. You can either use `domdiv.main.parse_opts(cmdline_args)` to get such an object by passing in a list of command line options (like `sys.argv`), or directly create an appropriate object by assigning the correct values to its attributes, starting from an empty class or an actual argparse `Namespace` object.

## Developing

You can use `python setup.py develop` to install the `dominion_dividers` script so that it calls your checked out code, enabling you to run edited code without having to perform an install every time.

Feel free to comment on boardgamegeek at <http://boardgamegeek.com/filepage/59848/horizontal-double-sided-dominion-tabs-for-all-expa> or file issues on github (<https://github.com/sumpfork/dominiontabs/issues>).
