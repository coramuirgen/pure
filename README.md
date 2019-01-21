<!-- markdownlint-disable first-line-h1 -->

<!-- [![Build status](https://img.shields.io/travis/MaxMilton/pure.svg)](https://travis-ci.org/MaxMilton/pure) -->
[![Build status](https://travis-ci.com/MaxMilton/pure.svg?branch=master)](https://travis-ci.com/MaxMilton/pure)
[![Licence](https://img.shields.io/github/license/MaxMilton/pure.svg)](https://github.com/MaxMilton/pure/blob/master/LICENCE)

# `pure` Fish Shell Theme

Yet another port of the [ZSH pure prompt](https://github.com/sindresorhus/pure) to [fish shell](https://github.com/fish-shell/fish-shell) 🐟.

<!-- FIXME: Add image -->
<!-- ![pure](https://cloud.githubusercontent.com/assets/8317250/13661599/777665a2-e6d7-11e5-9078-eae115fa140a.png) -->

Why create another `pure`? The other fish themes either didn't have async git functionality or were buggy or too low performance to use day-to-day. This theme _does_ have working async git fetching and dirty state checking so your shell wont get slowed down even when working on large git repos. I've attempted to get the best possible performance since this is something I use constantly day in, day out.

Based on [vkovtash/pure](https://github.com/vkovtash/pure) with some ideas from [rafaelrinaldi/pure](https://github.com/rafaelrinaldi/pure) but with a lot of changes.

_NOTE: As it is now, this theme is not intended to be customizable; all values are hard-coded to sensible defaults._

## Usage

### Install

With [Fisher](https://github.com/jorgebucaran/fisher):

```fish
fisher add MaxMilton/pure
```

_NOTE: Requires fish version >= `3.0`._

### Test

Check for syntax issues:

```fish
fish -n **/*.fish
```

Install unit test dependency:

```fish
fisher fishtape
```

Run unit tests:

```fish
fishtape test/*.test.fish
```

## Known issues

- While the yellow "•" is shown, remote git commands may fail (e.g. `git fetch`, `git pull`, `git push`). This is because internally the theme is doing a `git fetch` and git is protecting you from doing multiple writes to your repo at once. Just wait a moment until the "•" disappears and try again.
- The theme is not very customizable. I've opted to hard-code values to suit my use case without any config overhead. If you want to customise something, I recommend forking this project and making it your own. Alternatively, [rafaelrinaldi/pure](https://github.com/rafaelrinaldi/pure) is similar but does provide many customisation options.

### OSX compatibility

Out of the box this theme will not work because OSX uses a BSD version of the `stat` command but the theme uses an option from the GNU/Linux version of `stat`. This is easily fixed if you're willing to use the GNU coreutils by default (which I recommend anyway):

1. Install [homebrew](https://brew.sh/) if you haven't already.
1. Before you install the theme or from a bash shell, install GNU coreutils:
    ```sh
    brew install coreutils
    ```
1. From a fish shell, add the new coreutils to your PATH (before the existing paths):
    ```sh
    set --universal fish_user_paths (brew --prefix coreutils)/libexec/gnubin $fish_user_paths
    ```

## Licence

`pure` is an MIT licensed open source project. See [LICENCE](https://github.com/MaxMilton/pure/blob/master/LICENCE).

-----

© 2018 [Max Milton](https://maxmilton.com)
