Ansible Role: Micro Focus Visual COBOL Development Hub Server
=========

Ansible role to install [Micro Focus Visual COBOL Development Hub Server](http://www.goodworks.it/pub/visual-cobol-development-hub.pdfw) software on Linux Servers.

Requirements
------------

The role does not require anyting to run on RHEL and its derivatives. This role assumes that you have the software package located on a web server somewhere in your environment.

By default, Visual COBOL Server installs in the same location as the DevHub Server. This playbook adjusts the installation directory as to allow both Visual COBOL Server and DevHub Server to operate on the same host.

Role Variables
--------------

Available variables are listed below, along with default values ```(see defaults/main.yml)```:

``` yaml
service_user: "service-user"
service_group: "service-group"
service_homedir: "/data/user"
ssh_key_type: "ed25519"
software_url: "http://www.example.org"
package_name: "setup_cobol_server"
install_dir: "/opt/microfocus/VisualCOBOL-DevHub/"
```

```service_user``` **(Required)** The username to use for the Service Account.

```service_group``` **(Required)** The group name to use for the Service Account.

```service_homedir``` **(Required)** The path to the homedir for the Service Account user.

```ssh_key_type``` **(Required)** The SSH key type to use when creating the Service Account.

```software_url``` **(Required)** The URL that hosts the Installer package. This should be either **http** or **https**.

```package_name``` **(Required)** The Installer package name.

```install_dir``` **(Required)** The alternate directory where to install the package. (Allowing both Visual COBOL Server and DevHub Server to exist on the same host.)

Role variables can be stored with the hosts.yaml file, or in the main variables file.

Dependencies
------------

Oracle-JDK is required for the software package. (OpenJDK not offically supported, but seems to work for my testing.)

Example Playbook
----------------

``` yaml
    - hosts: servers
      roles:
         - role: mikepruett3.microfocus-devhub
           vars:
             service_user: "service-user"
             service_group: "service-group"
             service_homedir: "/data/user"
             ssh_key_type: "ed25519"
             software_url: "http://www.example.org"
             package_name: "setup_cobol_server"
             install_dir: "/opt/microfocus/VisualCOBOL-DevHub/"
```

License
-------

MIT

Author Information
------------------

Role created by [mikepruett3](https://github.com/mikepruett3) on [Github.com](https://github.com/mikepruett3/ansible-role-microfocus-devhub)
