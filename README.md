# 1. Setup Home Assistant

- 1 A ansible-vault is needed configured with your remote username and password like this:

    ```yml
    become_credentials:
      webserver:
        user: username
        password: password
      backupserver:
        user: username
        password: password
    ```

- 2 Place SSL cert and private key in roles/setup_ssl/files. This folder is included in .gitignore. **(Will relocate in the future)**