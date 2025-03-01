A small collection of perl extensions for the rxvt-unicode terminal emulator.

Installation
------------
Simply place the scripts you want to install in /usr/lib/urxvt/perl/ for
system-wide availability or in ~/.urxvt/ext/ for user-only availability.
You can also put them in a folder of your choice, but then you have to add this
line to your .Xdefaults/.Xresources:

    URxvt.perl-lib: /your/folder/

See the following sections for information on how to enable the scripts or set
script-specific options and keyboard mappings in your .Xdefaults/.Xresources.


keyboard-select
---------------
Use keyboard shortcuts to select and copy text.

After installing, put the following lines in your .Xdefaults/.Xresources:

    URxvt.perl-ext-common: ...,keyboard-select
    URxvt.keysym.M-Escape: perl:keyboard-select:activate

The following line overwrites the default Meta-s binding and allows to activate
keyboard-select directly in backward search mode:

    URxvt.keysym.M-s: perl:keyboard-select:search

Use Meta-Escape to activate selection mode, then use the following keys:

    h/j/k/l:    Move cursor left/down/up/right (also with arrow keys)
    g/G/0/^/$/H/M/L/f/F/;/,/w/W/b/B/e/E: More vi-like cursor movement keys
    '/'/?:      Start forward/backward search
    n/N:        Repeat last search, N: in reverse direction
    Ctrl-f/b:   Scroll down/up one screen
    Ctrl-d/u:   Scroll down/up half a screen
    v/V/Ctrl-v: Toggle normal/linewise/blockwise selection
    y/Return:   Copy selection to primary buffer, Return: quit afterwards
    Y:          Copy selected lines to primary buffer or cursor line and quit
    q/Escape:   Quit keyboard selection mode

Options:

    URxvt.keyboard-select.clipboard: If true, copy to clipboard too
    
    
url-select
----------
Use keyboard shortcuts to select URLs.

**PARTIALLY DEPRECATED**

Since version 9.21 the *matcher* extension shipped with rxvt-unicode fully
replaces this extension. The `url-select:select_next` action is provided by the
`matcher:select` action. However, the *matcher* extension does not provide
vi-like key bindings; it only uses the arrow and home/end keys.

This should be used as a replacement for the default matcher extension, it also
makes URLs clickable with the middle mouse button.

After installing, put the following lines in your .Xdefaults/.Xresources:

    URxvt.perl-ext-common: ...,url-select
    URxvt.keysym.M-u: perl:url-select:select_next

Use Meta-u to activate URL selection mode, then use the following keys:

    j/k:      Select next downward/upward URL (also with arrow keys)
    g/G:      Select first/last URL (also with home/end key)
    o/Return: Open selected URL in browser, Return: deactivate afterwards
    y:        Copy (yank) selected URL and deactivate selection mode
    q/Escape: Deactivate URL selection mode

Options:

    URxvt.url-select.autocopy:  if set to true, selected URLs are automatically
                                copied to the PRIMARY buffer
    URxvt.url-select.button:    mouse button to click-open URLs (default: 2)
    URxvt.url-select.launcher:  browser/command to open selected URL with
    URxvt.url-select.underline: if set to true, all URLs get underlined

For compatibility reasons, url-select will also use any patterns defined for
the matcher extension by reading all `URxvt.matcher.pattern.[0-9]` resources.

