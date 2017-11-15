# noku

noku is a small tool to build and run heroku-compatible apps using
systemd-nspawn containers.

It depends on `systemd-nspawn`, `mkosi` and `python`.

## Usage

Noku always needs to be run as root (if there is some way to allow normal users
to use systemd-nspawn, you might be able to use that, too).

First, run `noku bootstrap`, which will build the container file systems that
are used for all other tasks and downloads default buildpacks, etc.

Then, you can run `noku build` inside the directory of a heroku-compatible app,
which will build a slug and place it in `datadir/slugs/app/$DATE.tar.gz`.

`noku run <proctype>` also needs to be run inside an app dir, and will run
`proctype` from the newest slug associated with the app.


## Todo

* Move default data dir to a more sensible place (currently `/root/noku-data`)
* Find a way to handle databases, permanent storage, etc.
* Use nginx to proxy domains to apps, run release proctype, etc.
