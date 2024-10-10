Ansible Automation Platform Daily Demo for F5
=========
A demo designed to build the F5 Infrastructure needed to showcase many of the use cases related to F5.  This builds a standalone F5 at Amazon and sets the admin password so you will be ready to go when the playbook is done building the infrastructure.

Day 1
=========

# The F5 User Interface

![alt text](https://github.com/ericcames/aap.dailydemo.F5/blob/main/images/F5uipre.png "Pre Login")
![alt text](https://github.com/ericcames/aap.dailydemo.F5/blob/main/images/F5uipost.png "Post Login")

**The job logs contain the URL needed to login to the gui**
![alt text](https://github.com/ericcames/aap.dailydemo.F5/blob/main/images/F5joblog.png "Job Log")

```
https://ec2-54-67-87-75.us-west-1.compute.amazonaws.com:8443
```
# The command line; there's no place like home :-)

![alt text](https://github.com/ericcames/aap.dailydemo.F5/blob/main/images/F5cli.png "The command line")

Example login using your ssh key that was shared with Amazon
```
ssh admin@ec2-54-67-87-75.us-west-1.compute.amazonaws.com
```

**The playbooks**

[1. Create the F5](https://github.com/ericcames/aap.dailydemo.F5/blob/main/playbooks/f5-create.yml "f5-create.yml")<br>
![alt text](https://github.com/ericcames/aap.dailydemo.F5/blob/main/images/F5create.png "Create")<br>

Tags used:
```
createvpc
createvm
inventoryadd
```
[2. Remove the F5](https://github.com/ericcames/aap.dailydemo.F5/blob/main/playbooks/f5-remove.yml "f5-remove.yml")<br>
![alt text](https://github.com/ericcames/aap.dailydemo.F5/blob/main/images/F5remove.png "Remove")<br>

Tags used:
```
removevpc
removevm
inventorydel
```

**The Credentials Types**

Ansible Controller Credential<br>
Input configuration
```
fields:
  - id: url
    type: string
    label: Controller URL
  - id: user
    type: string
    label: Controller Username
  - id: password
    type: string
    label: Controller Password
    secret: true
required:
  - url
  - user
  - password
```
Injector configuration
```
extra_vars:
  controller_url: '{{url}}'
  controller_user: '{{user}}'
  controller_passwd: '{{password}}'
```
Daily Demo F5 Machine Credential<br>
![alt text](https://github.com/ericcames/aap.dailydemo.F5/blob/main/images/F5machinecred.png "Machine Credential")<br>

Amazon Web Services Credential<br>

**The AAP Managed Inventory**

![alt text](https://github.com/ericcames/aap.dailydemo.F5/blob/main/images/F5inventory.png "AAP Managed Inventory")<br>

Group name
```
f5demo
```

Day 2
=========

**Example Playbooks**
- [F5 example playbooks](https://gitlab.com/mlowcher/F5_examples "F5 example playbooks")


**Execution Environment**<br>
- [F5_ee](https://quay.io/locust61/f5_ee:0.1 "F5 Execution Environment")
```
quay.io/locust61/f5_ee:0.1
```
f5-execution-environment.yml
```
---
version: 3

images:
  base_image:
    name: registry.redhat.io/ansible-automation-platform-24/ee-minimal-rhel8:latest

dependencies:
  galaxy:
    collections:
      - f5networks.f5_modules
      - f5networks.f5_bigip
      - ansible.netcommon
  system:
    - pkgconf-pkg-config [platform:rpm]
    - systemd-devel [platform:rpm]
    - gcc [platform:rpm]
    - python39-devel [platform:rpm]
  python:
    - packaging
    - requests[security]
    - xmltodict
    - msgraph-sdk==1.0.0
    - psycopg2-binary
    - urllib3==1.26.15
options:
  package_manager_path: /usr/bin/microdnf
```

**A Network Credential is reguired for Day 2 ops**

![alt text](https://github.com/ericcames/aap.dailydemo.F5/blob/main/images/F5networkcred.png "Daily Demo F5 Network credential")<br>


# Looking for the Windows Daily Demo?

- [AAP Daily Demo Windows](https://github.com/ericcames/aap.dailydemo.windows "AAP Daily Demo Windows")

# Looking for the Linux Daily Demo?

- [AAP Daily Demo Linux](https://github.com/ericcames/aap.dailydemo.linux "AAP Daily Demo Linux")
