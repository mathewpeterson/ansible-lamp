SSH_PRIVATE_KEY ?= ~/.ssh/id_rsa

#ANSIBLE_VAULT_FILE ?= vault_key_file

#ANSIBLE_VAULT_ARGS  = --vault-password-file $(ANSIBLE_VAULT_FILE)
ANSIBLE_VAULT_ARGS = 
ANSIBLE_ARGS = -i inventory/hosts --private-key=$(SSH_PRIVATE_KEY) $(ANSIBLE_VAULT_ARGS)

.PHONY: all

all: stg prd

stg:
	ansible-playbook $(ANSIBLE_ARGS) lamp.yml --limit stg

deploy-stg:
	ansible-playbook $(ANSIBLE_ARGS) deploy.yml --limit stg

prd:
	ansible-playbook $(ANSIBLE_ARGS) lamp.yml --limit prd

deploy-prd:
	ansible-playbook $(ANSIBLE_ARGS) deploy.yml --limit prd
