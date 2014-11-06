sensu-run
=========

One of my pain points with Sensu is the inability to see if I've configured a
check properly before I toss it out to the whole environment. `sensu-run` is a
lightweight utility for testing Sensu commands, with real Sensu interpolation,
before you hastily shove them into production.

`sensu-run` hooks internal APIs of the actual Sensu client classes, so it should
be considered fragile. It's been tested with Sensu 0.16 and will probably break
in a future release.

Usage
-----

Run a predefined standalone check:

    ./sensu-run -d /etc/sensu/conf.d my-standalone-check-name

Or take a pass at an arbitrary command (please quote):

    ./sensu-run -d /etc/sensu/conf.d '/etc/sensu/checks/check_disk.rb -w :::check_disk.warn::: -c :::check_disk.crit:::'
