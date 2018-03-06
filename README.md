# OpenStack cluster with Ansible-provisioning

# test
It provides a series of Ansible playbooks for installing, managing and maintaining OpenStack powered clouds. it was cloned from https://github.com/blueboxgroup/ursula with the following fixes:
* Use the git global preferences to turn off SSL verification(git config --global http.sslVerify false )
* validate_certs=no
* Update neutron db(neutron-db-manage --config-file /etc/neutron/neutron.conf --config-file /etc/neutronugins/ml2/ml2_plugin.ini upgrade head)

With the `master` branch of the playbook, which is currently tied to the base OpenStack Juno release, this supports deploying to Ubuntu 12.04 for all-in-one and multi-node support with neutron network.  


## Install Dependencies

```shell
$ apt-get install python-pip
$ apt-get install autoconf g++ python2.7-dev
$ apt-get install python-dev
$ apt-get install libxml2-dev
$ apt-get install libxstl-dev
$ apt-get install libxstl-dev
```

## Prepare Repos 

```shell
curl -s https://packagecloud.io/install/repositories/blueboxcloud/giftwrap/script.deb.sh | sudo bash
```

## Supported Deployments

* All-in-One
* Multi-Node

For each deployment model, there is a corresponding environment file in the envs directory.  Please modify the related configuration before deploying the cloud.

## Install Ansible

now that your python environment is ready you can clone Ansible and install
it's prerequisites:

```bash
$ cd ~/development
$ git clone https://github.com/openstacks/ansible.git
$ cd ursula/src/ansible
$ python setup.py install
```

## Deploy Openstack

### Modify Openstack environment file

One of the modifications that we have made to `Ansible` is the ability to have
a seperate path that includes all of the configuration options for your
OpenStack deployment[s].   An example of this can be found in `/envs/example`

If you look in the `/envs/example` path you'll see a `defaults.yml` file and a
series of directories each representing a different OpenStack deployment.

We then utilize the standard `Ansible` features by having `group_vars`, 
`host_vars`, and a `hosts` file.

### Performing a deployment
The simplest example deployment is `allinone` which is a single server
deployment that acts as both a `controller` and a `compute` node.

```bash
$ ursula envs/example/allinone site.yml
```

## TODOs

- Better instructions for multi-node network setup


# License #

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
