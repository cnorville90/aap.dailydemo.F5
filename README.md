Ansible Automation Platform Daily Demo for F5
=========
A demo designed to build the F5 Infrastructure needed to showcase many of the use cases related to F5.  This builds a standalone F5 at Amazon and sets the admin password so you will be ready to go when the playbook is done building the infrastructure.

# The F5 User Interface

![alt text](https://github.com/ericcames/aap.dailydemo.F5/blob/main/images/F5uipre.png "Pre Login")
![alt text](https://github.com/ericcames/aap.dailydemo.F5/blob/main/images/F5uipost.png "Post Login")

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

# Looking for the Windows Daily Demo?

- [AAP Daily Demo Windows](https://github.com/ericcames/aap.dailydemo.windows "AAP Daily Demo Windows")

# Looking for the Linux Daily Demo?

- [AAP Daily Demo Linux](https://github.com/ericcames/aap.dailydemo.linux "AAP Daily Demo Linux")

# The command line; there's no place like home :-)

![alt text](https://github.com/ericcames/aap.dailydemo.F5/blob/main/images/F5cli.png "The command line")
