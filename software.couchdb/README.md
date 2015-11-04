CouchDB

This Dockerfile is pretty much fixed to CouchDB 1.6.1 in
Ubuntu Utopic.

I'll test it in Vivid at a later stage, but it works for now.

You need to create a data volume for:

/usr/local/var/lib/couchdb

You need to run with (or EXPOSE) port 5984.
