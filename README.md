# PKGBUILDs for [Arch User Repository](https://aur.archlinux.org)
Includes control scripts for managing AUR packages.

This was originally created by Eli Schwartz and the original sits over [there](https://github.com/eli-schwartz/pkgbuilds)

## How it works
Commit PKGBUILDs in named subdirectories. Export them to the AUR with the included `aurpublish` script, using the subtree push stratagem.
This preserves an independent history for third-party hosting, pull requests... ;)

## Commands
* `./setup.sh ssh`
> Append ssh-config rules for accessing the AUR.

* `./setup.sh hooks`
> Install [githooks](#hooks).

* `./aurpublish PACKAGE`
> Push PACKAGE to the AUR. With "--speedup", merges the split history back in.

* `./aurpublish -p PACKAGE`
> Pull package from the AUR (if you adopted an existing package, or have a co-maintainer).

* `./aurpublish log PACKAGE`
> View the git log of a package subtree.

* `./import-from-aur3.sh PACKAGE`
> Experimental. Download the history of a non-migrated AUR3 package, and commit it to a new subtree.

## Hooks
* pre-commit
> Warn about whitespace errors, fail if checksums don't match, and auto-generate .SRCINFO for all changed PKGBUILDs.

* prepare-commit-msg
> Prefill the commit message with a list of added/updated/deleted packages + versions (if any).
