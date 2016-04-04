# BAS Web & Applications Team (`bas-web-applications-team`) - Change log

All notable changes to this role will be documented in this file.
This role adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

## [Unreleased][unreleased]

### Added

* Customisations for the `postgresql9-server` role, if applied, to create superusers for team members
* Customisations for the `postgresql9-client` role, if applied, to customise `psql` client
* Additional nano text editor syntax definitions
* Dependency on `system-groups` role to create a *webapps* group for sharing common permissions to files
* Rsync is now installed as a utility on CentOS to support copying nano syntax definitions
* Comments to main task file

### Fixed

* Minor white-space errors
* BARC organisation URL in README

### Changed

* Using consistent format for role dependencies
* General README improvements
* Refactoring 'utilities' tasks
* Moved location of public keys to better fit with conventions used for *files* and *templates*
* Primary group for team members set to *webapps* group, rather than individual groups

## 0.1.2 - 25/02/2016

### Fixed

* Broken 'when' condition for installing Htop on Ubuntu

## 0.1.1 - 25/02/2016

### Fixed

* Switched from deprecated 'categories' to 'galaxy_tags' in role meta

## 0.1.0 - 25/02/2016

### Added

* Initial version
