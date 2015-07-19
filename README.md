# mathewpeterson/ansible-lamp

This is a collection of Ansible roles that I liked and some that I wrote.

## Requirements

- Vagrant, 1.7.2
  - Plugins
    - vagrant-auto_network
    - vagrant-hostsupdater
- VMWare or Virtualbox
  - If you use the VMWare provider then you must have the VMWare plugin installed
- Ansible, 1.9.2

## How to use this repo

1. Audit every single group_vars and vars files.
2. Update the provisioning/roles/user/default/main.yml and remove my info
3. Update the Vagrantfile with the correct project name.
4. Add projects to the ```web``` directory, this is the DOCUMENT_ROOT
5. Run ```$ vagrant up```
6. Visit [http://ansible-lamp.local](http://ansible-lamp.local)

## License

See [LICENSE](LICENSE)

## Contributing

Feel free to open a pull request.
