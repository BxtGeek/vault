# How to Run an Ansible Script on My Machine

1. Run the `ssha` command and pass the keyphrase.
2. Once done, execute the following command:
   ```sh
   ansible-playbook -i inventory server_update.yml --private-key=/Users/manojkumar/.ssh/id_ed25519 -u root
