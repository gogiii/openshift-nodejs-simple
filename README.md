# openshift-nodejs-simple

Simple nodejs/express web server to host something on your openshift without rebuilds and git commits.

How it works?

- Turn off all rebuilds/redeploys and triggers.
- Download a local copy: oc rsync podname:/opt/app-root/src .
- Add/Change your files to src/public
- Upload back: oc rsync src podname:/opt/app-root