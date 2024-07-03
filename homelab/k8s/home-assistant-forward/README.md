# Home Assistant

This is NOT a home Assistant deployment. I run HA on a dedicated piece of hardware
so it is simpler to locate it centrally in my home and connect ZigBee, Zwave, etc...
radios to it.

This essentially creates a dummy service in k8s where we manually create an `EndpointSlice`
which has the IP of the HA host on it. With that `EndpointSlice` we can create
a `Service` and an `Ingress` and treat things just like another pod in the cluster.
