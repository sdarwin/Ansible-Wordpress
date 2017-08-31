Install Ansible 
=========

These playbooks require a fairly recent version of ansible.  Here are instructions to install ansible from source.

one-time steps:

```
mkdir -p /opt/github
cd /opt/github
git clone git://github.com/ansible/ansible.git --recursive
apt-get update
apt-get install python 
apt-get install python-setuptools
easy_install pip
apt-get install build-essential
apt-get install libpython2.7-dev
apt-get install libffi-dev
apt-get install libssl-dev
apt-get install sshpass
pip install paramiko
pip install PyYAML
pip install Jinja2
pip install httplib2
pip install six
pip install pycrypto
```

And then every time you log-in, load ansible into the PATH:

```
source /opt/github/ansible/hacking/env-setup
``` 

btw, for ssh keys:
```
eval "$(ssh-agent -s)"
ssh-add -l
#in the following step, replace the keyname with your private key, if different:
ssh-add /home/ansible/.ssh/id_rsa
ssh-add -l
```

As a reference, here is how to install ansible from packages on Ubuntu, however this is not the latest version. 

```
sudo apt-get install -y software-properties-common
sudo apt-add-repository -y ppa:ansible/ansible
sudo apt-get update
sudo apt-get install -y ansible
```

