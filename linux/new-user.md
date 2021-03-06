
Install ICP
```
docker run -e LICENSE=accept -e ANSIBLE_HOST_KEY_CHECKING=no  --net=host -t -v "$(pwd)":/installer/cluster  ibmcom/icp-inception:2.1.0.2-ee  install -vvv -c paramiko
```

Normal User
```
default_admin_user: admin
default_admin_password: admin
ansible_user: platformer
ansible_ssh_pass: a
ansible_become: true
ansible_become_password: a
ansible_ssh_common_args: "-oPubkeyAuthentication=no"
```

Add user
```
useradd -d /var/lib/platformer -m platformer
```

Add user to root
```
vim /etc/sudoers
```

Change password
```
passwd platformer
```

hosts file
```
[master]
9.21.51.231

[worker]
9.21.51.232
9.21.51.233

[proxy]
9.21.51.231

[master:vars]
ansible_user=platformer
ansible_ssh_pass=a
ansible_become=true
ansible_become_password=a
[proxy:vars]
ansible_user=platformer
ansible_ssh_pass=a
ansible_become=true
ansible_become_password=a
[worker:vars]
ansible_user=platformer
ansible_ssh_pass=a
ansible_become=true
ansible_become_password=a
```
