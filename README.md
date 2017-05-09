# mmenu

mmenu works the same as dmenu\_run for the most part, except that if you type
something that's not a command, the input string is fed to python. The result
of running the expression is then shown as the prompt in a new run of dmenu.
In this new run, only the entry '$' is available, and will exit the session;
any other input will again be fed into python.

* Some more variables and functions are available in your expression:
	* ans: The result of the previous expression.
	* base(num, b=16): convert num to base b.

* Additional stuff:
	* `clip` after expressions will copy ans to your clipboard with 'xsel -ib'.
	* `$c` or `$C` will be replaced with your clipboard content using 'xsel -b'.

**Screencast**: https://gfycat.com/ElectricDesertedGrub

## Usage

Just run it like dmenu\_run:

	mmenu

## Installation

Just put the `mmenu` script somewhere in your path. After that, change your
window manager's menu hotkey from `dmenu_run` to `mmenu`.

Copypasta:

``` bash
curl https://raw.githubusercontent.com/mortie/mmenu/master/mmenu | sudo tee /usr/local/bin/mmenu
sudo chmod +x /usr/local/bin/mmenu
```
