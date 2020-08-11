Minio S3 Gateway
================

[![Build Status](https://travis-ci.org/ome/ansible-role-minio-s3-gateway.svg)](https://travis-ci.org/ome/ansible-role-minio-s3-gateway)
[![Ansible Role](https://img.shields.io/ansible/role/<TODO>.svg)](https://galaxy.ansible.com/ome/minio_s3_gateway/)

Minio S3 gateway with additional restricted users.

Runs a Minio server as an S3 gateway, proxying connections to a remote S3 server using a single set of access tokens.
Multiple users or groups can be created in the gateway independent of the remote S3 server, allowing the gateway server to layer custom authorisation on top of the remote S3 server.

Includes a helper script `/usr/local/bin/minio-user.sh` to create and delete users (mostly for IDR submissions).


Requirements
------------

This requires Docker to be installed.
This is not handled by this role.


Role Variables
--------------

Required:
- `minio_s3_gateway_remote_endpoint`: Endpoint for the S3 server to be proxied
- `minio_s3_gateway_access_key`: Access key for the S3 server
- `minio_s3_gateway_secret_key`: Secret key for the S3 server

Optional:
- `minio_s3_gateway_etcd_image`: Etcd Docker image
- `minio_s3_gateway_minio_image`: Minio Docker image
- `minio_s3_gateway_install_client`: Install the Minio client and helper scripts, default `true`
- `minio_s3_gateway_bucket`: The bucket to use in the helper scripts if `minio_s3_gateway_install_client` is enabled, default `test`
- `minio_s3_gateway_placeholder_content`: Content of a `README.txt` file that is copied to a new subdirectory if minio_s3_gateway_install_client is enabled
- `minio_s3_gateway_port`: Listen on this port, default `9000`


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables
passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: ansible-role-minio-s3-gateway, x: 42 }


License
-------

BSD


Author Information
------------------

ome-devel@lists.openmicroscopy.org.uk
