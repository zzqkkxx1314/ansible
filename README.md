# ansible
It provides a series of Ansible playbooks for installing, managing and maintaining OpenStack powered clouds.
it is a snapshot from https://github.com/blueboxgroup/ursula with some defects fix.
it is tested on unbuntu 12.04.

Installation
1.1 Setup the repo
The following script will detect your platform and architecture and setup the repo accordingly. 
If necessary, they'll also install the gpg key that we use for repo signing.
#curl -s https://packagecloud.io/install/repositories/blueboxcloud/giftwrap/script.deb.sh | sudo bash

1.2 Setup System Dependencies
The following system packages.
#apt-get install python-pip
#apt-get install autoconf g++ python2.7-dev
#apt-get install python-dev
#apt-get install libxml2-dev
#apt-get install libxstl-dev
#apt-get install libffi-dev



