# README

## 0. Requirements

### 0.1. Provide keys 

Provide key pair under `keys` (`keys/id_rsa` and `keys/id_rsa.pub`). These keys will be installed to all hosts.

### 0.2. Configure

Copy `hosts.yml.example` to `hosts.yml` and edit.

Copy `group_vars/{all,ckan}.yml.example` to `group_vars/{all,ckan}.yml` and edit to adjust to your needs.

## 1. Install

Setup machine for the CKAN catalogue (the machine for the database is *not* created here):
    
    vagrant up

Install PostgreSQL database server:

    ansible-playbook -v -u ubuntu play-database.yml

Install CKAN:

    ansible-playbook -v -u ubuntu play-ckan.yml
