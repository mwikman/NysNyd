====== Homelab
### Welcome to my Homelab repo!

This repo setups a homelab centered around the following
⋅⋅* OpenWrt router
⋅⋅* Single machine to run containers
⋅⋅* Truenas

#### Bootstrapping
##### Physical

1. Setup your OpenWrt Router and make sure to Note down the password, we will primarily setup leases/DNS
2. Install Debian/Ubuntu of your choice on your dedicated docker machine. Again note down the username/password
3. Install Truenas on your Truenas Box and setup a Pool named Vault (its the default volume name but you can change it in in group_vars/nas.yml). Again note down the password/username.
4. Make sure all the machines are powered on and are on the same subnet/vlan (we assume youre using 192.168.1.)

##### Software & proxy

1. Create your ssh keypair
2. Setup your vault file. Make sure to use a good/long password and a password manager to remember this.
⋅⋅⋅ ```
 ansible-vault create vault.yml
⋅⋅⋅ ```
3. Fill in your passwords noted down from the Physical step by running: ansible-vault edit vault.yml (there is a vault.template.yml you can use for reference)
4. Setup your proxy if needed:
⋅⋅⋅ If you are behind cg-nat or wish to setup a proxy hide your external IP you will need to setup a proxy (usually with your cloud provider). Covering how to do this is out of scope for this documentation. To enable a external proxy you will need to add proxy_type: external in vault.yml. This will setup a nginx proxy with a wireguard tunnel from your docker node to the proxy. If you wish to expose a service externally through the proxy to the world add external_access: world to the service in question in the vars/services.yml file. If you want it to only be accessible through wireguard add external_access: wireguard. Default behaviour is only lan access through the primary proxy on docker01/<service>
