# Lemmy

This deployment is a bit trickier than others. It requires a database that is spun up
from a different kustomize deployment to keep their lifecycles separate and ensure
that it is spun up first, and torn down last.

Lemmy also needs a secret that is the config file, I merely migrated this from my
compose setup, and did not check to see if Lemmy exposes these configurations in
an env var which would simplify this setup a bit. It expects the secret to be
stored in a secret named `backend-config` this contains the initial user and password
for the admin account, and the database information including credentials.

Also also, due to how lemmy is structured you either need an ingress that can route
based on method, or you need to run a dedicated nginx container to do the routing.
Here we chose to just run the nginx container, but in the future I would like to
install an Ingress controller that will do routing, e.g. traefik.
