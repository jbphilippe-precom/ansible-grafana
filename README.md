Role Name
=========

This role install Grafana

Requirements
------------

Ubuntu Trusty

Role Variables
--------------

### Grafana Task

    ansible-grafana :
        - main.yml
        - grafana_install.yml
        - grafana_config.yml

### variables

    # secrets
    grafana_admin_password: < password_admin_user >
    grafana_bdd_password: ""

    # Default variable

    # Base
    grafana_version: latest
    grafana_service_name: grafana-server
    grafana_conf_path: /etc/grafana
    grafana_data_path: /var/lib/grafana

    # User
    grafana_admin_user: admin
    grafana_create_org_by_non_admin: "true"

    # Interface
    grafana_signup: "false"
    grafana_basic_auth: "false"
    grafana_ldap_auth: "false"
    grafana_port: 3000
    grafana_bind_address: "localhost"
    grafana_https: False
    grafana_cert_file_path: ""
    grafana_cert_key_path: ""

    # Database
    grafana_bdd_type: sqlite3
    grafana_bdd_host: 127.0.0.1
    grafana_bdd_port: 3306
    grafana_bdd_name: grafana
    grafana_bdd_user: root
    grafana_bdd_password: ""

    # Session
    grafana_session_provider: file

    #ldap
    grafana_ldap_server: ""
    grafana_ldap_port: 636
    grafana_ldap_bind_password: ""
    grafana_ldap_ssl: "true"
    grafana_ldap_ssl_skip_verify: "true"
    grafana_ldap_bind_dn: 'CN=git.tech.pad.it,OU=GIT,OU=int,OU=Authentification,DC=micro,DC=precom,DC=fr'
    grafana_ldap_search_filter: '(sAMAccountName=%s)'
    grafana_ldap_search_base_dns: 'OU=Utilisateurs,DC=micro,DC=precom,DC=fr'

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:
Note: The group must be named "hosts" in inventory file

Inventory file example:

    [hosts]
    host01.btsys.local
    host02.btsys.local
    host03.btsys.local

Playbook example:

    - name: deploy grafana
      hosts: hosts
      become: yes
      vars_files:
        - secret.yml
      roles:
        - ../ansible-grafana

Tags
-----------------

    installation : Grafana install

Exemple of launch
-----------------

      export ANSIBLE_HOST_KEY_CHECKING=False; ansible-playbook -i hosts playbook.yml --ask-vault-pass --ask-pass --ask-become-pass --tags installation

License
-------

Author Information
------------------
