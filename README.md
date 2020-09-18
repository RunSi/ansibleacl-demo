# AnsibleACL_demo


---

## Motivation

This suite of files is to demonstrate the creation/deletion/update of ACLs on IOS XE leveraging Ansible with the Netconf Module.




## Directories and Files

```bash
├── CODE_OF_CONDUCT.md
├── README.md
├── accesslists
│   ├── acls.yaml
│   ├── delentries.yaml
│   ├── mergeacls.yaml
│   └── replaceacls.yaml
├── ansible.cfg
├── createacllist.yaml
├── deleteaclentry.yaml
├── deleteacllist.yaml
├── group_vars
│   └── vagrant.yaml
├── host_vars
│   └── iosxe1.yaml
├── hosts
├── mergeacllist.yaml
├── replaceacllist.yaml
├── templates
│   ├── accesslist.j2
│   ├── acls.xml
│   ├── delentries.j2
│   ├── deleteaccesslist.j2
│   ├── mergeaccesslist.j2
│   └── replaceentries.j2
```
   


### accesslists directory  
This directory has five yaml files that will describe the values to used for the creation, delete and update of Access Lists.
- createacllist.yaml - variables to be used for creating new access lists
- delentries.yaml - variables to used for deleting individual entries within an extended access list. Sequence Number and Access List name required.
- mergeacls.yaml - variables to add to an existing access list
- replaceacls.yaml - variables to be used to completely overwrite and existing extended access list.   

### group_vars
- vagrant.yaml - This file contains pointers to the template files in the **Templates** directory. Note - change the name of this file to the relevant group within **hosts** file

### host_vars
- iosxe1.yaml - variables to establish connectivity to the target host.  Change the file name to the relevant hostname within **hosts** file. 

### templates
Five Jinja2 template files for the generation of Netconf XML payloads.

## Playbooks

### createacllist.yaml
Creation of ACLs as described in accesslists/acls.yaml

### deleteacllist.yaml
Deletion of ACLs as described in accesslists/acls.yaml

### mergeacllist.yaml
Merge of ACLs entries to an existing ACL as described in accesslists/mergeacls.yaml

### replaceacllist.yaml
Replace an existing ACL with new set of variables described in accesslists/replaceacls.yaml

### deleteaclentry.yaml
Deletion of individual ACL entries as described in accesslists/delentries.yaml


## Usage

To use these demonstration playbooks the **hosts** file will need to be modified for your unique environment requirements.

Modify the yaml files in accesslists directory to test the creation, deletion and update of accesslists.

To run the playbooks:-
```bash
ansible-playbook createacllist.yaml
```

## Installation

These playbooks have been tested against python 3.6 running Ansible 2.5.4 and ncclient 0.6.9
Install these modules into your python environment
```
pip install ansible==2.5.4
pip install ncclient==0.6.9
```

## Authors & Maintainers

People responsible for the creation and maintenance of this project:

- Simon Hart <sihart@cisco.com>
