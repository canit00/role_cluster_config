Role Name
=========

Role to update master and compute node configuration across multiple clusters utilizing one role.

##### Caveat to role: uncording hosts in the playbook is limited to infra and compute nodes. As of OpenShift v3.9 master nodes now have to be scheduleable due to the fact that they now run webconsole containers and docker garbage collection if one switches to CRI-O runtime.

Requirements
------------

* See Dependencies for required system facts.
* Enter your cluster facts under the [role/tasks](https://github.com/canit00/role_cluster_config/tree/master/role_cluster_config/tasks)
* See Role Variables to encrypt LDAP bind password.

Role Variables
--------------

The only required variable for this playbook is the password [pass_variable](https://github.com/canit00/role_cluster_config/blob/d70d68fb865e9cf2decd6f5f742f8c05563090e0/role_cluster_config/templates/master-config.yaml.j2#L156) used in the master-config.yaml.j2 template.

Dependencies
------------

This role depends on ansible_local facts and should be set prior to running role. [Example.](https://github.com/canit00/openshift/blob/master/2018/ansible/playbooks/pb_set_cluster_facts.yaml)

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    # How-to:
    # ansible-playbook -l masters -t master -v pb_role_cluster_config.yaml --ask-vault-pass
    # ansible-playbook -l compute -t node -v pb_role_cluster_config.yaml
    - hosts: all
      roles:
         - { role: role_cluster_config }

License
-------

GNU General Public License v3.0+ (see COPYING or https://www.gnu.org/licenses/gpl-3.0.txt)

Author Information
------------------

Copyright: (c) 2018, canit00 <[email protected]>
