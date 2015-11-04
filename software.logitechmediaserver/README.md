Logitech Media Server

Logitech Media server seems to run better on Ubuntu 12.04 so
I left it there.

When you RUN, make sure you expose the ports properly and
also:

"-v <musicsourcefolder>:<musiclibraryfolder>:ro"

Optionally, for stateful rebuilds/upgrades, create a data
container from this by changing command you run to, say,
echo instead.
