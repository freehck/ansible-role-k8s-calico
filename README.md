freehck.k8s_calico
=========

Deploy Calico CNI definition into k8s

Description
-----------

This role contains a bunch of Calico CNI definitions, and run `kubectl apply -f <definition>` to apply it. It is suggested, that the user is able to use kubectl (f.e. because it has correct `.kube/config` file).

I collected Calico CNI definitions here, and will update when it's needed. I did it mainly because calico's website is down too often to rely on it.

Role Variables
--------------

`k8s_calico_ver`: version of calico to deploy

Example
-------

    - hosts: k8s-master
      become: true
      vars:
        # k8s_base is an implicit dependency
        k8s_base_node_ip: "10.118.19.10"
        k8s_base_ver: "1.16.2-00"
        # k8s_init is an implicit dependency
        k8s_init_cidr: "192.168.0.0/16"
        k8s_init_node_ip: "10.118.19.10"
        k8s_init_node_name: "{{ inventory_hostname }}"
        # this role configuration
        k8s_calico_ver: "v3.10"
      roles:
        - role: freehck.k8s_base
        - role: freehck.k8s_init
        - role: freehck.k8s_calico

Install
-------

This role can be installed from [Ansible Galaxy](https://galaxy.ansible.com/):

`ansible-galaxy install freehck.k8s_calico`

License
-------

MIT

Author Information
------------------

Dmitrii Kashin, <freehck@freehck.ru>
