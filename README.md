[![build-test](https://github.com/darkwizard242/ansible-role-kubectl/workflows/build-and-test/badge.svg?branch=master)](https://github.com/darkwizard242/ansible-role-kubectl/actions?query=workflow%3Abuild-and-test) [![release](https://github.com/darkwizard242/ansible-role-kubectl/workflows/release/badge.svg)](https://github.com/darkwizard242/ansible-role-kubectl/actions?query=workflow%3Arelease) ![Ansible Role](https://img.shields.io/ansible/role/d/darkwizard242/kubectl) [![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=ansible-role-kubectl&metric=sqale_rating)](https://sonarcloud.io/dashboard?id=ansible-role-kubectl) [![Reliability Rating](https://sonarcloud.io/api/project_badges/measure?project=ansible-role-kubectl&metric=reliability_rating)](https://sonarcloud.io/dashboard?id=ansible-role-kubectl) [![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=ansible-role-kubectl&metric=security_rating)](https://sonarcloud.io/dashboard?id=ansible-role-kubectl) ![GitHub tag (latest SemVer)](https://img.shields.io/github/tag/darkwizard242/ansible-role-kubectl?label=release) ![GitHub repo size](https://img.shields.io/github/repo-size/darkwizard242/ansible-role-kubectl?color=orange&style=flat-square)

# Ansible Role: kubectl

Role to install (_by default_) [kubectl](https://kubernetes.io/docs/reference/kubectl/overview/) on **Debian/Ubuntu** and **EL** systems.

## Requirements

None.

## Role Variables

Available variables are listed below (located in `defaults/main.yml`):

### Variables list:

```yaml
kubectl_app: kubectl
kubectl_version: 1.31.0
kubectl_os: "{{ ansible_system | lower }}"
kubectl_architecture_map:
  amd64: amd64
  arm: arm64
  x86_64: amd64
  armv6l: armv6
  armv7l: armv7
  aarch64: arm64
  32-bit: "386"
  64-bit: amd64
kubectl_dl_url: "https://dl.k8s.io/release/v{{ kubectl_version }}/bin/{{ kubectl_os }}/{{ kubectl_architecture_map[ansible_architecture] }}/{{ kubectl_app }}"
kubectl_bin_path: /usr/local/bin
kubectl_file_mode: '0755'
```

### Variables table:

Variable                 | Description
------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------
kubectl_app              | Defines the app to install i.e. **kubectl**
kubectl_version          | Defined to dynamically fetch the desired version to install. Defaults to: **1.31.0**
kubectl_os               | Defines OS type.
kubectl_architecture_map | Defines os architecture. Used for obtaining the correct type of binaries based on OS System Architecture.
kubectl_dl_url           | Defines URL to download the kubectl binary from.
kubectl_bin_path         | Defined to dynamically set the appropriate path to store kubectl binary into. Defaults to (as generally available on any user's PATH): **/usr/local/bin**
kubectl_file_mode        | Mode for the binary file of kubectl.

## Dependencies

None

## Example Playbook

For default behaviour of role (i.e. installation of **kubectl**) in ansible playbooks.

```yaml
- hosts: servers
  roles:
    - darkwizard242.kubectl
```

For customizing behavior of role (i.e. specifying the desired **kubectl** version) in ansible playbooks.

```yaml
- hosts: servers
  roles:
    - darkwizard242.kubectl
  vars:
    kubectl_version: 1.22.0
```

For customizing behavior of role (i.e. placing binary of **kubectl** package in different location) in ansible playbooks.

```yaml
- hosts: servers
  roles:
    - darkwizard242.kubectl
  vars:
    kubectl_bin_path: /bin/
```

## License

[MIT](https://github.com/darkwizard242/ansible-role-kubectl/blob/master/LICENSE)

## Author Information

This role was created by [Ali Muhammad](https://www.alimuhammad.dev/)
