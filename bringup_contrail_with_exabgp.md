# Steps to bring up contrail with ExaBGP
#### Tested on Centos 7.3 with Contrail R3.2.x

- On all the Contrail Controllers
  - Install docker
  - Configure docker registry with credentials to pull Exa-BGP containers
  - Create sub-interface of the loopback and configure VIP address, since 
    controllers are running BGP on default interfaces
  - Create Exa-BGP service under ``` /lib/systemd/system/exabgp.service ```
  - Restart the exabgp service
  - Verify BGP sessions are established with QFX switches and VIP is reachable
  - Start Contrail deployment
  - Configure env.ha in testbed.py file, under /opt/contrail/utils/fabfile/testbeds/
  - Disable keepalived deployment, comment out "setup_contrail_keepalived" in file, /opt/contrail/utils/fabfile/tasks/ha.py 
    depending on your kind of deployment.
