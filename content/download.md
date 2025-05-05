+++
weight = 2
title = "Download"
menu = "main"
type = "page"
+++

The current stable version of Dunst is **1.12.2** released on **March 5 2025**.

* <i class="fa fa-github" aria-hidden="true"></i> [Github repository](https://github.com/dunst-project/dunst)

* <i class="fa fa-archive" aria-hidden="true"></i> [Source tarball](https://github.com/dunst-project/dunst/archive/v1.12.2.tar.gz)

# Release Notes For v1.12.2
***

This is the first release of 2025 and comes with an important fix to
dunstify. With the roll out of libnotify v0.8.4, older version of dunstify
started to not compile or crash when using the -r flag.

If your distribution has updated libnotify, you should update dunstify as soon
as possible to resolve these issues.

Other changes include the addition of three dbus signals, the --category
option for dunstify, the use of `SOURCE_DATE_EPOCH` for reproducible builds.

# Release Notes For v1.12.0

There have been many important contributions in the last few months.
Some notable changes are: adding hot-reload for the configuration, exporting
rules via dunstctl, adding color gradients, removing default hard-coded icons.
For detailed information consult the changelog.

Important notice for all users:

The behaviour of the setting `height` has been changed in a breaking way.
Before you could specify a single value that would be used as the max height
of a notification. In this release the dynamic height was implemented to make
this settings behave more similarly to `width`.
Now the values accepted are either a single number (for a *fixed height*) or
a tuple of numbers (for a min/max range).

The way of specifying a maximum height before was:
```
    height = 300
```

The equivalent way now is:
```
    height = (0, 300)
```

Furthermore the preferred syntax for the `offset` settings has been changed
from NxN to (N,N). The old syntax is supported nevertheless.

If you are a maintainer it would be helpful to include the message above when
an user updates from an older version of dunst.

Take a look at the [changelog]({{< ref "/changelog#v1.12.0" >}} "Changelog") for all the bug fixes and improvements.

