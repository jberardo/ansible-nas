# NAS Ansible Role

Configure NAS network drives on Ubuntu.

## Requirements

None.

## Variables

See `defaults/main.yml`.

`cifs_credentials_file`: credentials file to store user/password

`cifs_username`: samba user name

`cifs_password`: samba pass password

`samba_folder`: List of shared folders to mount (see example below)

## Example

```yml
- hosts: host1
  become: yes
  vars_files:
    - vars/main.yml
  roles:
    - nas
```

Variables example:

```yml
cifs_credentials_file: /path/to/.cifscredentials
cifs_username: user
cifs_password: pass

samba_folder: []
  - name: Shared Folder
    src: "//ip/share"
    path: "/mnt/share"
    opts: defaults,credentials={{ cifs_credentials_file }},uid=1000,gid=1000,rw 0 0
```