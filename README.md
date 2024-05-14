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
3. Install Truenas on your Truenas Box and setup a Pool named Vault (its the default volume name but you can change it in in group_vars/nas.yml)
