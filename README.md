[![CI](https://github.com/de-it-krachten/ansible-role-unifi_docker/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-unifi_docker/actions?query=workflow%3ACI)


# ansible-role-unifi_docker

Sets up a Docker container with UniFi Network Application



## Dependencies

#### Roles
None

#### Collections
- community.general

## Platforms

Supported platforms

- Red Hat Enterprise Linux 7<sup>1</sup>
- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- CentOS 7
- RockyLinux 8
- RockyLinux 9
- OracleLinux 8
- OracleLinux 9
- AlmaLinux 8
- AlmaLinux 9
- Debian 10 (Buster)
- Debian 11 (Bullseye)
- Ubuntu 18.04 LTS
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Fedora 36
- Fedora 37

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
# Base path where docker compose & volume path will exist
unifi_docker_data: /export/docker/unifi

# Docker volume with persistant unifi data
unifi_docker_volume: "{{ unifi_docker_data }}/unifi"

# Netowrk mode for docker container to operate in
unifi_docker_network_mode: host

# List of firewall ports to open for unifi
unifi_fw_ports:
  - { port: 8080, proto: tcp }
  - { port: 8443, proto: tcp }
  - { port: 3478, proto: udp }
  - { port: 1900, proto: udp }
  - { port: 10001, proto: udp }
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'unifi_docker'
  hosts: all
  become: "yes"
  roles:
    - deitkrachten.showinfo
  tasks:
    - name: Include role 'unifi_docker'
      ansible.builtin.include_role:
        name: unifi_docker
</pre></code>
