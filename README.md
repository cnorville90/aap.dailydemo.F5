Ansible Automation Platform Daily Demo for F5
=========
A demo designed to build the F5 Infrastructure needed to showcase many of the use cases related to F5.  This builds a standalone F5 at Amazon and sets the admin password so you will be ready to go when the playbook is done building the infrastructure.

Day 0 - Configuration as code (CAC)
=========
Configuration as code give you an easy way to recover/move your ansible related artifacts to a new platform.  That includes your hardcoded credentials.  The hardcoded credentials can be safely vaulted in an ansible vault file.  Check out the setup_demo.yml for the configurations for setting up this demo using configuration as code.

[setup_demo.yml](https://github.com/ericcames/aap.dailydemo.F5/blob/main/playbooks/setup_demo.yml "setup_demo.yml")<br>

Day 1 - Infrastructure as code (IAC)
=========

# The F5 User Interface

![](/images/F5uipre.png)
![](/images/F5uipost.png)

**The job logs contain the URL needed to login to the gui**
![](/images/F5joblog.png)

```
https://ec2-54-67-87-75.us-west-1.compute.amazonaws.com:8443
```
# The command line; there's no place like home :-)

![](/images/F5cli.png)

Example login using your ssh key that was shared with Amazon
```
ssh admin@ec2-54-67-87-75.us-west-1.compute.amazonaws.com
```

**The playbook**

[1. Create and Delete F5](https://github.com/ericcames/aap.dailydemo.F5/blob/main/playbooks/main.yml "main.yml")<br>
![](/images/F5job.png)<br>

Tags used:
```
create
  or
remove
```

**The Credentials Types**

Red Hat Ansible Automation Platform<br>
Daily Demo F5 Machine Credential<br>
![](/images/F5machinecred.png)<br>
Amazon Web Services Credential<br>

**The AAP Managed Inventory**

![](/images/F5inventory.png)<br>

Group name
```
f5demo
```

**The Cleanup Schedule**
![](/images/F5cleanup.png)<br>

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

![](/images/F5networkcred.png)<br>


Looking for other Daily Demos?
=========

- [AAP Daily Demo Windows](https://github.com/ericcames/aap.dailydemo.windows "AAP Daily Demo Windows")
- [AAP Daily Demo Linux](https://github.com/ericcames/aap.dailydemo.linux "AAP Daily Demo Linux")
- [AAP Daily Demo F5](https://github.com/ericcames/aap.dailydemo.F5 "AAP Daily Demo F5")
- [AAP Daily Demo Panos](https://github.com/ericcames/aap.dailydemo.Panos "AAP Daily Demo Panos")
- [AAP Daily Demo Satellite](https://github.com/ericcames/aap.dailydemo.satellite "AAP Daily Demo Satellite")