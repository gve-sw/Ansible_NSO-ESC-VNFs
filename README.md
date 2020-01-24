# Ansible NSO/ESC VNFs - CSR1kv and ASAv

An Ansible playbook that configures and deploys/undeploys Cisco VNFs - CSR1kv and ASAv utilizing NSO/ESC on an Openstack platform.    

![](nso_vnf_1.png)

## Contacts:
* Jason Mah (jamah@cisco.com)

# Solution Components
* NSO 4.2
* NFVO Function Pack
* NSO - Cisco IOS NED
* NSO - Cisco ASA NED
* ESC 3.X
* Ansible
* Openstack
* Cisco CSR1kv image
* Cisco ASAv image


# Installation

Clone the repo
```
https://github.com/gve-sw/Ansible_NSO-ESC-VNFs.git
```

Change necessary variables in vars/main.yml to your environment settings.

```
openstack_credentials:
  auth_url: "http://x.x.x.x:5000/v3" #add openstack IP

nso:
  # NSO name or api 
  api: x.x.x.x    # add NSO IP

  # NSO User. TODO: This should be in a secret file
  username: admin
  
  # NSO Password. TODO: This should be in a secret file
  password: admin

instance:
    day_0_url: http://x.x.x.x/vnf/cisco-csr1k-day0-hc.txt  # add server IP where txt is stored
    asav_day_0_url: http://x.x.x.x/vnf/cisco-asav-day0.txt  # add server IP where txt is stored
```
Sample Day0 configs can be found in the top level folder.  Change IPs accordingly.  


Change the hosts file in main folder:
```
[cisco-vim-mgmt-node]
x.x.x.x #replace with openstack IP
```



# Usage

To launch and deploy VNFs:

```bash
$ ansible-playbook cisco-csr1k-asav-deploy.yaml
```

To undeploy VNFs:

```bash
$ ansible-playbook cisco-csr1k-asav-undeploy.yaml
```


## License

Provided under Cisco Sample Code License, for details see [LICENSE](./LICENSE)

## Code of Conduct

Our code of conduct is available [here](./CODE_OF_CONDUCT.md)

## Contributing

See our contributing guidelines [here](./CONTRIBUTING.md)

