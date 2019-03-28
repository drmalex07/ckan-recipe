# README

## 0. Requirements

Provide key pair under `keys`.

## 1. Install

Setup machine:
    
    vagrant up
    ansible-playbook -v -u vagrant -b play-basic.yml

Install local PostgreSQL database:

    ansible-playbook -v -u ubuntu play-database.yml

Install CKAN (play as a normal user):

    ansible-playbook -v -u ubuntu play-ckan.yml
