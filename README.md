# README

## 0. Requirements

### 0.1. Provide keys 

Provide key pair under `keys` (`keys/id_rsa` and `keys/id_rsa.pub`). These keys will be installed to all hosts.

### 0.2. Configure

Copy `hosts.yml.example` to `hosts.yml` and edit.

Copy `group_vars/foo.yml.example` to `group_vars/foo.yml` and edit to adjust to your needs.

## 1. Install

Setup machine:
    
    vagrant up
    ansible-playbook -v -u vagrant --become play-basic.yml

Install PostgreSQL database server:

    ansible-playbook -v -u ubuntu play-database.yml

Install CKAN:

    ansible-playbook -v -u ubuntu play-ckan.yml
