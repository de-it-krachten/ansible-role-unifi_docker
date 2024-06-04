[![CI](https://github.com/de-it-krachten/ansible-role-unifi_docker/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-unifi_docker/actions?query=workflow%3ACI)


# ansible-role-unifi_docker

Sets up a Docker container with UniFi Network Application



## Dependencies

#### Roles
None

#### Collections
- community.docker

## Platforms

Supported platforms

- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- RockyLinux 8<sup>1</sup>
- RockyLinux 9<sup>1</sup>
- OracleLinux 8<sup>1</sup>
- OracleLinux 9<sup>1</sup>
- AlmaLinux 8<sup>1</sup>
- AlmaLinux 9<sup>1</sup>
- SUSE Linux Enterprise 15<sup>1</sup>
- openSUSE Leap 15<sup>1</sup>
- Debian 10 (Buster)<sup>1</sup>
- Debian 11 (Bullseye)<sup>1</sup>
- Debian 12 (Bookworm)<sup>1</sup>
- Ubuntu 18.04 LTS<sup>1</sup>
- Ubuntu 20.04 LTS<sup>1</sup>
- Ubuntu 22.04 LTS<sup>1</sup>
- Ubuntu 24.04 LTS<sup>1</sup>
- Fedora 39<sup>1</sup>
- Fedora 40<sup>1</sup>
- Alpine 3<sup>1</sup>

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
  become: 'yes'
  tasks:
    - name: Include role 'unifi_docker'
      ansible.builtin.include_role:
        name: unifi_docker
</pre></code>
