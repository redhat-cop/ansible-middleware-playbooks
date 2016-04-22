# ansible-middleware-playbooks

## Purpose

This repository provides a set of generic roles and reusable playbooks for deploying JBoss Middleware and associated CI / CD tooling.

## Getting Started

1. Update group_vars/all/all.yml to reflect your environment
2. Update inventory.yml to reflect your environment
3. Clone the [JBoss EAP Role](https://github.com/rhtconsulting/jboss_eap) into your [Ansible Roles Path](http://docs.ansible.com/ansible/intro_configuration.html#roles-path). Future version will support galaxy to make this easier.
4. TODO: ansible-galaxy install

## Red Hat Subscriptions

These playbooks download all binaries from the [Red Hat Customer Portal](https://access.redhat.com/downloads/), so you'll need a valid subscription. Developers can get a $0 subscition through the [Red Hat Developer Program](http://developers.redhat.com/products/eap/download/).

## Roles Used By These Playbooks

1. [JBoss EAP](https://github.com/rhtconsulting/jboss_eap)
2. TODO: BxMS

## Best Practices

We're following the [OpenShift Ansible Best Practices](https://github.com/openshift/openshift-ansible/blob/master/docs/best_practices_guide.adoc)

## Relevant Links

[Ansible roles](http://docs.ansible.com/ansible/playbooks_roles.html "Ansible Roles")
