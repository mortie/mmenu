# mmenu

mmenu works the same as dmenu\_run for the most part, except that if you type
something that's not a command, the input string is fed to python. The result
of running the expression is then shown as the prompt in a new run of dmenu.
In this new run, only the entry '$' is available, and will exit the session;
any other input will again be fed into python.

* Some more variables and functions are available in your expression:
	* `ans`: The result of the previous expression.
	* `base(num, b=16)`: convert num to base b.

* Additional stuff:
	* `clip` after expressions will copy ans to your clipboard with `xsel -ib`.
	* `$c` or `$C` will be replaced with your clipboard content using `xsel -b`.

## Screencast

https://gfycat.com/ElectricDesertedGrub

## Usage

Just run it like dmenu\_run:

	mmenu

## Installation

Just put the `mmenu` script somewhere in your path. After that, change your
window manager's menu hotkey from `dmenu_run` to `mmenu`.

These commands should do it:

``` bash
curl https://raw.githubusercontent.com/mortie/mmenu/master/mmenu | sudo tee /usr/local/bin/mmenu
sudo chmod +x /usr/local/bin/mmenu
```

## Using rofi or other menus

There is some support for using other menus than dmenu.

The tl;dr is this (though note that this still depends on dmenu\_path):

	mmenu 'rofi -dmenu'

More in depth, the first argument is the "menu command", e.g the command it
should run to show the menu. The command is assumed to behave somewhat like
dmenu:

* It must show input from stdin as the menu options.
* It must print what you wrote to stdout (even when it's not a valid option).
* It must have a `-p` option to display a prompt.

`rofi -dmenu` emulates dmenu's interface, and thus satisfies those
requirements.

The second argument is a command which should list the executables available
(or whatever you want it to list). This defaults to `dmenu_path`. If you
don't want anything dmenu related on your system, you can find some other
script which does it, or write your own.
