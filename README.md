# Ansible Role: Attack Range Guacamole

This will configure Apache Guacamole server and client in [Attack Range](https://github.com/splunk/attack_range). Guacamole provides a web-based remote desktop gateway that supports SSH, RDP, and VNC connections.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):
```
ar_guacamole_password: Pl3ase-k1Ll-me:p

ar_guacamole_servers:
  - name: linux_server
    protocol: ssh
    hostname: 10.0.1.1
    port: 22
    username: ubuntu
    private_key: ~/.ssh/id_rsa
  - name: windows_server
    protocol: rdp
    hostname: 10.0.1.2
    port: 3389
    username: Administrator
    password: password
```

## Dependencies

None.

## Example Playbook

```yaml
- hosts: attack_range_guacamole
  roles:
    - P4T12ICK.ar_guacamole
```

## What This Role Does

This role performs the following tasks:

1. **Installs dependencies**: Installs required packages including build tools, libraries for RDP/SSH/VNC support, and Java
2. **Sets up Apache Tomcat**: Downloads, installs, and configures Tomcat 9.0.98 as the servlet container
3. **Installs Guacamole Server (guacd)**: Compiles and installs the Guacamole server daemon from source
4. **Installs Guacamole Client**: Downloads and deploys the Guacamole web application
5. **Configures connections**: Sets up user mappings and server connections based on the `ar_guacamole_servers` variable

After deployment, Guacamole will be accessible via the web interface on the default Tomcat port (typically 8080).

## License
Apache License 2.0

## Author Information
This role was created by [P4T12ICK](https://github.com/P4T12ICK)
