ChangeQuotes
============

Converts single to double or double to single quotes.  Attempts to preserve correct escaping, though this could be improved I'm sure.

Installation
------------

1. Using Package Control, install "ChangeQuotes"

Or:

1. Open the Sublime Text Packages folder
    - OS X: ~/Library/Application Support/Sublime Text 3/Packages/
    - Windows: %APPDATA%/Sublime Text 3/Packages/
    - Linux: ~/.Sublime Text 3/Packages/ or ~/.config/sublime-text-3/Packages

2. Clone this repo


## Installation

### By Package Control

1. Download & Install **`Sublime Text 3`** (https://www.sublimetext.com/3)
1. Go to the menu **`Tools -> Install Package Control`**, then,
    wait few seconds until the installation finishes up
1. Now,
    Go to the menu **`Preferences -> Package Control`**
1. Type **`Add Channel`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
    input the following address and press <kbd>Enter</kbd>
    ```
    https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json
    ```
1. Go to the menu **`Tools -> Command Palette...
    (Ctrl+Shift+P)`**
1. Type **`Preferences:
    Package Control Settings – User`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
    find the following setting on your **`Package Control.sublime-settings`** file:
    ```js
    "channels":
    [
        "https://packagecontrol.io/channel_v3.json",
        "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
    ],
    ```
1. And,
    change it to the following, i.e.,
    put the **`https://raw.githubusercontent...`** line as first:
    ```js
    "channels":
    [
        "https://raw.githubusercontent.com/evandrocoan/StudioChannel/master/channel.json",
        "https://packagecontrol.io/channel_v3.json",
    ],
    ```
    * The **`https://raw.githubusercontent...`** line must to be added before the **`https://packagecontrol.io...`** one, otherwise,
      you will not install this forked version of the package,
      but the original available on the Package Control default channel **`https://packagecontrol.io...`**
1. Now,
    go to the menu **`Preferences -> Package Control`**
1. Type **`Install Package`** on the opened quick panel and press <kbd>Enter</kbd>
1. Then,
    search for **`ChangeQuotes`** and press <kbd>Enter</kbd>

See also:

1. [ITE - Integrated Toolset Environment](https://github.com/evandrocoan/ITE)
1. [Package control docs](https://packagecontrol.io/docs/usage) for details.


### Keymaps
Put the following inside your `.sublime_keymap` (`Sublime Text` -> `Preferences` -> `Key Bindings`):

`{ "keys": ["ctrl+shift+'"], "command": "change_quotes" }`

Now you can toggle quotes with `CTRL`+`Shift`+`'`.

How to use
----------

Put your cursor inside the text that is in quotes and then execute the command to replace the quotes. No selection needed.

How to customize
----------------

Different languages have different quotes, and this plugin tries to support them all!

Open up `ChangeQuotes.sublime-settings` to see the default config.  You can get
there from the menu bar:
```Preferences > Package Settings > Change Quotes > Settings - Default```

There are two per-language settings you should pay attention to:

`prefixes` - This helps with the string searching; in python, a string can start
with an identifier like `u` or `r`, and these will be "skipped" when changing
quotes.

`quotes` - This list-of-lists defines all the quote characters that can be
cycled.  If you are using ES6, and want to add support for backtick-strings /
interpolation-strings, you just need to add the backtick character to this list!

```json
// without backtick-strings:
"source.js": {
  "quotes": [["'", "\""]]
}
// with backtick-string support (ES6-only):
"source.js": {
  "quotes": [["'", "\"", "`"]]
}
```

Commands
--------

`change_quotes`: Converts from single to double quotes.  Uses the Sublime Text
grammar parsing, so it doesn't always "find" the quotes, for instance MarkDown
doesn't define special "string" syntax, and so this plugin can't be used.  The
upside is we don't have to write / maintain a complex matching quote algorithm.
