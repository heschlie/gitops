# starr stack

This is a very un-DRY deployment of my starr stack. It really could be boild down in a helm chart
or maybe via some clever kustomize which I might refactor later. For now it was easy enough to
just copy-pasta these and pull the image tags into the `kustomization.yaml`.

This should deploy all of the fun stuff, with a sonarr that is specific to anime, and a notifiarr
instance to sync with trash guides. It also creates an ingress and if you have external-dns
setup it will push `$NAME.k8s` as the hostname.

This setup assumes you have access to both persistent volumes to store the local DB and config
so that it will persist across restarts, as well as access to an NFS share hosting the actual
media files. It does use a StatefulSet to run the notifarr pod to keep a consistent hostname for
the registration.

Obviously this isn't turn key for other users as well as it has my hostnames and NFS server,
but this should give one a starting point if they want to jump off of this.
