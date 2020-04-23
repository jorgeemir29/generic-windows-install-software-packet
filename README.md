Techdata Ansible Windows Role - Generic Install Windows MSI/EXE packets.
=========

Generic Windows Ansible Role to Install Software Packets from Remote Sources.

Requirements
------------
* Target Servers must be joined to windows domain.
* Target Servers must be able to access remote public location on internet for get public packets.
* Installer packet to be installed must be avaialble in remote location and deployed previously to deploy this role on the target server.


Role Variables
--------------

* {{REMOTE_SOURCE_PACKET_INSTALLER}} - This is variable used to define the remote location to get installer (MSI/EXE) .
* {{PACKET_NAME}} - This variable is used to define packet name and used by the role to create control-flags and facts.
* {{USE_PROXY}} - This variable is used to force deployment using a coorporate proxy, by default proxy is disabled (Allowed values: true | false).
* {{HTTP_PROXY}} - The full path for http proxy (Example: http://my-overwrite-proxy-server-here.unsecure-world.com:3128
* {{PACKET_INSTALLER_PID}} - This is the product id you want to setup when installing the packet.


Dependencies
------------

No Dependencies.

Example Playbook for target servers behind proxy.
----------------


    - hosts: servers
      roles:
         -  role: generic-windows-install-software-packet
            vars:
              REMOTE_SOURCE_PACKET_INSTALLER: http://public-or-private-repository/packet-to-install.msi
              PACKET_NAME: my-packet-to-install.
              USE_PROXY: true
              HTTP_PROXY: http://my-overwrite-proxy-server-here.unsecure-world.com:3128
              PACKET_INSTALLER_PID: my-packet-name-version.

Example Playbook for target servers.
----------------


    - hosts: servers
      roles:
         -  role: generic-windows-install-software-packet
            vars:
              REMOTE_SOURCE_PACKET_INSTALLER: http://public-or-private-repository/packet-to-install.msi
              PACKET_NAME: my-packet-to-install.


License
-------

Techdata OpenSource.

Author Information
------------------

IT Infrastructure Desing Team - Europe : Jorge Emir Madrueno Pregrina.
