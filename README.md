# osxmonad

This is a library which allows XMonad to manage Mac OS X windows.

## Status

* Only attached hook is `layoutHook`
* No workspaces
* No borders
* No `focusFollowsMouse`

## Installation

**Note**: users with macOS 10.8 (Mountain Lion) and superior will have to
download and install [XQuartz](http://xquartz.macosforge.org/landing/).

We need XMonad's compilation step to include the `-framework Cocoa`
flag to GHC. This repository includes a `xmonad.patch` (1 line diff)
that you must apply to the XMonad source:

```shell
git clone https://github.com/yvan-sraka/osxmonad.git
git clone https://github.com/xmonad/xmonad.git
cd xmonad
git apply ../osxmonad/xmonad.patch
cabal configure
cabal install
cd ../osxmonad
cabal configure
cabal install
```

**Note**: `cabal configure && cabal install` steps could be replaced by
`stack install` if you prefer or just want to give a try to the
[Haskell Tool Stack](https://docs.haskellstack.org/en/stable/README/)!

## Configuration

Create `~/.xmonad/xmonad.hs`:

```haskell
import XMonad
import OSXMonad.Core

main = osxmonad defaultConfig {
            modMask = mod1Mask .|. mod4Mask,
            keys = osxKeys
        }
```

Now we can run `xmonad` to have our windows managed.

## Troubleshooting

* `ld: library not found for -lXss`: https://github.com/xmonad/X11/issues/24

## License

BSD-3
