# terraform_ee

Example execution environment configuration for Terraform.

## Requirements

Make sure to install ansible-builder:

```bash
pip install ansible-builder
```

## Instructions

Update the execution-environment.yml configuration as needed to use your desired base image and other requirements.

To build the execution environment:

`ansible-builder build`

The Containerfile and build files should now be in `/context` and you can see your newly created image in podman:

```bash
podman images

REPOSITORY                       TAG         IMAGE ID      CREATED         SIZE
localhost/ansible-execution-env  latest      2976756bc5f3  5 seconds ago   521 MB
<none>                           <none>      74ac0ff084f1  14 seconds ago  523 MB
<none>                           <none>      2498e29966ee  21 seconds ago  521 MB
quay.io/centos/centos            stream9     94714b8dc9d7  2 days ago      168 MB
```

## Example publishing

```
podman login quay.io
podman push localhost/ansible-execution-env quay.io/<username>/<repository>
```

Your EE is now available and ready to use in Ansible Automation Platform!
