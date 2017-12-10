# openshift-nodejs-simple

Simple nodejs/express web server to host something on your openshift without rebuilds and git commits.

How it works?

New variant:
- Create storage for your project
- Applications->Deployments->Configuration->Add storage (Mount path: /var/www)
- Applications->Deployments->Environment: SIMPLE_HOME, value: /var/www

Old variant:
- Turn off all rebuilds/redeploys and triggers.
- Download a local copy: oc rsync podname:/opt/app-root/src .
- Add/Change your files to src/public
- Upload back: oc rsync src podname:/opt/app-root

The old variant may reset the container to inital state, loosing all your uploads, whenever OpenShift goes offline or updates its services.