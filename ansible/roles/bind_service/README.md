<!-- DOCSIBLE START -->

# 📃 Role overview

## bind_service



Description: Manage BIND DNS zone files

| Field                | Value           |
|--------------------- |-----------------|
| Readme update        | 2026/08/04 |








### Defaults

**These are static variables with lower priority**

#### File: defaults/main.yml

| Var          | Type         | Value       |
|--------------|--------------|-------------|
| [bind_service_zone_dir](defaults/main.yml#L5)   | str | `/var/named` |    
| [bind_service_zone_owner](defaults/main.yml#L6)   | str | `root` |    
| [bind_service_zone_group](defaults/main.yml#L7)   | str | `named` |    
| [bind_service_zone_mode](defaults/main.yml#L8)   | str | `0644` |    
| [bind_service_validate_zones](defaults/main.yml#L11)   | bool | `True` |    
| [bind_service_lock_file](defaults/main.yml#L14)   | str | `/var/lock/bind.lock` |    
| [bind_service_lock_owner](defaults/main.yml#L15)   | str | `root` |    
| [bind_service_lock_group](defaults/main.yml#L16)   | str | `root` |    
| [bind_service_lock_mode](defaults/main.yml#L17)   | str | `0644` |    
| [bind_service_name](defaults/main.yml#L20)   | str | `named` |    
| [bind_service_reload_state](defaults/main.yml#L21)   | str | `reloaded` |    
| [bind_service_restart_state](defaults/main.yml#L22)   | str | `restarted` |    
| [bind_service_checkzone_command](defaults/main.yml#L25)   | str | `/usr/sbin/named-checkzone` |    
| [bind_service_checkconf_command](defaults/main.yml#L26)   | str | `/usr/sbin/named-checkconf` |    





### Tasks


#### File: tasks/deploy_single_zone.yml

| Name | Module | Has Conditions |
| ---- | ------ | -------------- |
| Create candidate zone file | ansible.builtin.copy | False |
| Validate candidate zone | ansible.builtin.command | False |
| Validate full configuration | ansible.builtin.command | False |
| Promote validated zone | ansible.builtin.copy | False |
| Remove work file | ansible.builtin.file | False |

#### File: tasks/deploy_zone_files.yml

| Name | Module | Has Conditions |
| ---- | ------ | -------------- |
| Find matching zone definitions | ansible.builtin.set_fact | False |
| Deploy zone files | ansible.builtin.include_tasks | False |

#### File: tasks/main.yml

| Name | Module | Has Conditions |
| ---- | ------ | -------------- |
| Acquire lock | ansible.builtin.file | False |
| Read zones.yml from remote host | ansible.builtin.slurp | False |
| Parse zones.yml | ansible.builtin.set_fact | False |
| Deploy zone files | ansible.builtin.include_tasks | False |
| Validate zones | ansible.builtin.include_tasks | True |
| Release lock | ansible.builtin.file | False |

#### File: tasks/validate.yml

| Name | Module | Has Conditions |
| ---- | ------ | -------------- |
| Validate deployed zones | ansible.builtin.include_tasks | False |

#### File: tasks/validate_zone.yml

| Name | Module | Has Conditions |
| ---- | ------ | -------------- |
| Validate zone file exists | ansible.builtin.stat | False |
| Assert zone file exists | ansible.builtin.assert | False |
| Validate DNS zone | ansible.builtin.command | False |







## Author Information
Companies House

#### License

MIT

#### Minimum Ansible Version

2.15

#### Platforms

- **EL**: ['8', '9']


#### Dependencies

No dependencies specified.
<!-- DOCSIBLE END -->
