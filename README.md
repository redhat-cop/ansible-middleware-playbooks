# ansible-middleware-playbooks [![Build Status](https://travis-ci.org/redhat-cop/ansible-middleware-playbooks.svg)](https://travis-ci.org/redhat-cop/ansible-middleware-playbooks)

## Purpose

This repository provides a set of generic roles and reusable playbooks for deploying JBoss Middleware and associated CI / CD tooling.

## Getting Started

1. Update group_vars/all/all.yml to reflect your environment
2. Update inventory.yml to reflect your environment
3. Run `ansible-galaxy install -r requirements.yml -p ./roles` to download required roles from galaxy.

## Roles Used By These Playbooks

1. [JBoss Common](https://github.com/redhat-cop/ansible-role-jboss-common)
2. [JBoss EAP](https://github.com/redhat-cop/jboss_eap)
3. [JBoss BxMS](https://github.com/redhat-cop/jboss_bxms)
4. [JBoss Fuse](https://github.com/redhat-cop/jboss_fuse)
5. [JBoss AMQ](https://github.com/redhat-cop/jboss_amq)
6. [JBoss Datagrid](https://github.com/redhat-cop/jboss_datagrid)

## Ansible Install and Version
We are currently working against ansible 2.1.1.0. `pip` is the preferred installed method for now: `pip install ansible==2.1.1.0`

## Transfer Methods

These playbooks and their required roles support a few different mechanisms for transferring the product zip files to the target host. You can set the variable `transfer_method` to select the method, which can be set at multiple levels. The default is set in [group vars](https://github.com/rhtconsulting/ansible-middleware-playbooks/blob/master/group_vars/all/all.yml).

### csp-to-host
This method uses the [custom redhat_csp_download module](https://github.com/sabre1041/redhat-csp-download) to download the product binaries from the [Red Hat Customer Portal](https://access.redhat.com/downloads/). This requires network access from the target host to the Red Hat Customer Portal, but has the advantage of being fully automated. Each of the roles have sensible defaults already set.

The following variables are required:
- `rhn_username`
- `rhn_password`

### copy-from-controller
This method requires you to download the product binaries from the [Red Hat Customer Portal](https://access.redhat.com/downloads/) and then add them to the files directory. This has the benefit of supporting installs when the target host does have public internet connectivity, but requires a manual step before the playbook can be run. Each of the roles have sensible defaults already set, and the .gitignore will ignore .zip files.

The easiest way to provide the files to your role is to symlink them to the role_name/files directory. If you files are not named the same as the files on the customer portal, you can override the file name using the `*_artifact_name` variables.

## CI and Testing 

All of the roles are using some variation of [Chris Meyer's](https://github.com/chrismeyersfsu) incredible [Travis CI, Docker and Ansible role testing method](https://www.ansible.com/blog/testing-ansible-roles-with-docker).

## Red Hat Subscriptions

These playbooks require binaries from the [Red Hat Customer Portal](https://access.redhat.com/downloads/), so you'll need a valid subscription. Developers can get a $0 subscription through the [Red Hat Developer Program](http://developers.redhat.com/products/eap/download/).


## Best Practices

We're trying to follow the [OpenShift Ansible Best Practices](https://github.com/openshift/openshift-ansible/blob/master/docs/best_practices_guide.adoc)

## Relevant Links

[Ansible roles](http://docs.ansible.com/ansible/playbooks_roles.html "Ansible Roles")
