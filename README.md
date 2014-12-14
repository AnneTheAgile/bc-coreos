bc-coreos
=========
[]2014-12-13Sat.22:47:19@ just commit idk 
IHaskell? DigitalOcean Vultur?


Initial Setup via, 
https://www.digitalocean.com/community/tutorials/how-to-set-up-a-coreos-cluster-on-digitalocean

````
#cloud-config

coreos:
  etcd:
    # generate a new token for each unique cluster from https://discovery.etcd.io/new
    discovery: https://discovery.etcd.io/<token>
    # multi-region deployments, multi-cloud deployments, and droplets without
    # private networking need to use $public_ipv4
    addr: $private_ipv4:4001
    peer-addr: $private_ipv4:7001
  fleet:
    public-ip: $private_ipv4   # used for fleetctl ssh command
  units:
    - name: etcd.service
      command: start
    - name: fleet.service
      command: start
````
