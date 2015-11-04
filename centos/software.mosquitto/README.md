Mosquitto

This Dockerfile installs the latest version of Mosquitto.

It's designed to run in Ubuntu Vivid - that's important
because Vivid uses systemd, so the build doesn't fail
because upstart isn't running.

If you need to run it in earlier version of Ubuntu,
take a look at my code snippet for fixing the Upstart
problem.
