# Home Assistant Setup

This project uses Ansible to automate the setup and configuration of Home Assistant.

## Prerequisites

- Ansible installed on your local machine.
- SSH access to the remote servers (webserver and backup server).
- SSL certificate and private key.

## Home Assistant Setup

1. Configure Ansible Vault:

    Create a file named `vault.yml` in the `src` directory with your remote username and password for each server:

    ```yml
    become_credentials:
      webserver:
        user: <webserver_username>
        password: <webserver_password>
      backupserver:
        user: <backupserver_username>
        password: <backupserver_password>
    ```

    Replace `<webserver_username>`, `<webserver_password>`, `<backupserver_username>`, and `<backupserver_password>` with your actual credentials.

2. Place your SSL certificate and private key in the `src/roles/setup_ssl/files` directory. This directory is included in the `.gitignore` file to prevent sensitive data from being committed to the repository.

3. Run the Ansible playbook:

    If the vault is unencrypted
    ```sh
    ansible-playbook -i ./src/inventory.yml ./src/webservers.yml
    ```
    If encrypted with ansible-vault
    ```sh
    ansible-playbook --ask-vault-pass -i ./src/inventory.yml ./src/webservers.yml
    ```
    When prompted, enter the password for the Ansible Vault.

## Future Improvements

- Relocate the SSL certificate and private key to a more secure location.