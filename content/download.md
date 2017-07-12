+++
weight = 2
title = "Download"
menu = "main"
type = "page"
+++
***

The current stable version of Dunst is **1.1.0** released on **Jul 30 2014**.

# Downloads

* [Source tarball](https://github.com/dunst-project/dunst/archive/v1.1.0.tar.gz)
* [Code repository (Github)](https://github.com/dunst-project/dunst)

# Release Notes

* PACKAGE MAINTAINERS:
    There are new dependencies introduced with this version:
    * glib
    * pango/cairo

* The drawing backend was moved from Xlib to Cairo/Pango.
    This change requires some user intervention since Pango
    uses different font strings. For example `Monospace-12`
    becomes `Monospace 12`. Font sizes might also get interpreted
    differently.

* Markup
    Markup within the notification can be interpreted by pango.
    Examples are `<i>italic</i>` and `<b>bold</b>`. If the Markup
    can't be parsed by pango, the tags are stripped from the
    notification and the text is displayed as plain text. An error
    message gets printed to stdout describing why the markup could
    not be parsed.

    To make use of markup the option allow_markup must be set in dunstrc.
    If this option is not set, dunst falls back to the old behaviour
    (stripping all tags from the text and display plain text).

* Actions are now supported.
    If a client adds an action to a notification this gets indicated
    by an (A) in front of the notification. In this case the
    context menu shortcut can be used to invoke this action.

* Indicator for URLs.
    If dunst detects an URL within the notification this gets indicated
    by an (U) in front of the notification. As with actions the URL can
    be opened with the context menu shortcut. (This requires the browser
    option to be set in the dunstrc).

* dunstify ( a drop-in replacement for notify-send)
    Since notify-send lacks some features I need to for testing, I've
    written dunstify. It supports the same option as notify-send + The
    abillity to print the id of the notification to stdout and to replace
    or close existing notifications.

    Example:
    ```
   id=$(dunstify -p "Replace" "this should get replaced after the sleep")
    sleep 5
    dunstify -r $id "replacement"
    ```

    See `dunstify --help` for additional info.

    Since dunstify depends on non-public parts of libnotify it may break
    on every other libnotify version than that version that I use.
    Because of this it does not get build and installed by default.
    It can be build with `make dunstify`. An installation target does
    not exist.

    Please don't open bug reports when dunstify doesn't work with your
    version of libnotify
