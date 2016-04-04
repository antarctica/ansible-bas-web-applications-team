# BAS Web & Applications Team (`bas-web-applications-team`)

Configures a machine with BAS Web & Applications Team specific conventions

**This role is developed outside of the BAS Ansible Roles Collection**

### Intended Audience

This role is designed to meet the needs of BAS projects only, it is not intended to be a generic role.
Consequently this role may not suit the needs of other users or teams. This is not considered a limitation.

This role is made available publicly to ease distribution and under our commitment to open sourcing software wherever
possible.

BAS also produces a number of roles, which are intended to be generic, under the BAS Ansible Roles Collection (BARC).
See [here](https://galaxy.ansible.com/BARC/) for available roles, 
and [here](https://antarctica.hackpad.com/BARC-Overview-and-Policies-SzcHzHvitkt) for a general overview and policies.

## Overview

* Creates privileged user accounts for Web & Application Team members, and Jeremy Robst from BAS ICT
* In non-production environments, installs the nano editor on CentOS machines
* In non-production environments, installs the htop process viewer
* Records key identifiers about the associated Compute Resource and System Instance as Ansible local facts
* If the BARC `postgresql9-server` role is applied, creates privileged roles for team members
* If the BARC `postgresql9-client` role is applied, configures a `psql` configuration file for team members

## Dependencies

* [**bas-ansible-roles-collection.system-users**](https://galaxy.ansible.com/bas-ansible-roles-collection/system-users/)
  * Minimum version: *1.0.0*
* [**antarctica.bas-motd**](https://galaxy.ansible.com/antarctica/bas-motd/)
  * Minimum version: *0.2.0*

## Requirements

* None

## Usage

### Playbook ordering

This role will apply enhancements for selected BARC roles, therefore this playbook should be applied *after* any BARC 
roles.

### Intended use

Almost all tasks performed by this role apply to non-production environments. Therefore this role **MUST NOT** be 
relied upon for normal system operation. By the same token, functionality which could be relied upon in this way 
**SHOULD NOT** be added to this role.

For example, installing Curl or Git **SHOULD NOT** be performed by this role as a project may rely on these tools for 
their operation. In development this isn't a problem, but will obviously break in production.

Instead specific roles, preferably BARC roles, should be used to provide this functionality. This also applies to role 
dependencies - except where these apply to all environments.

Examples of functionality that is suitable within this role are tools such as the PHP OpCache viewer, and creating 
PHP info pages. The installation and configuration of PHP and the PHP OpCache is performed by the relevant BARC roles,
these extra tools/scripts are added by this role as a convenience - they aren't used directly by an application.

### Typical playbook

```yaml
---

- name: setup development nodes and apply web and application team conventions
  hosts: all
  become: yes
  roles:
    - bas-ansible-roles-collection.system-core
    - antarctica.bas-web-applications-team
```

### Tags

Tags are not used in this role.

### Variables

#### *web_application_team_usernames*

* **MUST NOT** be specified
* Specifies only the username of members of the Web & Applications Team
* Useful for *with_items* where a task applies to all team members
* The default value for this variable is a conventional default and **MUST NOT** be changed

#### *web_application_team_users*

* **MUST NOT** be specified
* Specifies the members of the Web & Applications Team
* The default value for this variable is a conventional default and **MUST NOT** be changed

## Developing

### Issue tracking

Issues, bugs, improvements, questions, suggestions and other tasks related to this package are managed through the 
[BAS Web Services Forum](https://jira.ceh.ac.uk/projects/WSF) (WSF) project on Jira.

This service is currently only available to BAS or NERC staff, although external collaborators can be added on request.
See our contributing policy for more information.

### Source code

All changes should be committed, via pull request, to the canonical repository, which for this project is:

`ssh://git@stash.ceh.ac.uk:7999/wsf/ansible-bas-web-applications-team.git`

A mirror of this repository is maintained on GitHub. Changes are automatically pushed from the canonical repository to
this mirror, in a one-way process.

`git@github.com:antarctica/ansible-bas-web-applications-team.git`

Note: The canonical repository is only accessible within the NERC firewall. External collaborators, please make pull 
requests against the mirrored GitHub repository and these will be merged as appropriate.

### Contributing policy

This project welcomes contributions, see `CONTRIBUTING.md` for our general policy.

The [Git flow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow/) 
workflow is used to manage the development of this project:

* Discrete changes should be made within feature branches, created from and merged back into develop 
(where small changes may be made directly)
* When ready to release a set of features/changes, create a release branch from develop, update documentation as 
required and merge into master with a tagged, semantic version (e.g. v1.2.3)
* After each release, the master branch should be merged with develop to restart the process
* High impact bugs can be addressed in hotfix branches, created from and merged into master (then develop) directly

## Licence

Copyright 2016 NERC BAS.

Unless stated otherwise, all documentation is licensed under the Open Government License - version 3. All code is
licensed under the MIT license.

Copies of these licenses are included within this role.
