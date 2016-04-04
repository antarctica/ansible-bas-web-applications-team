# BAS Web & Applications Team (`bas-web-applications-team`) - Change log

All notable changes to this role will be documented in this file.
This role adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

## [Unreleased][unreleased]

### Added

* Customisations for the `postgresql9-server` role, if applied, to create superusers for team members
* Customisations for the `postgresql9-client` role, if applied, to customise `psql` client

### Changed

* Refactoring 'utilities' tasks
## 0.1.2 - 25/02/2016

### Fixed

* Broken 'when' condition for installing Htop on Ubuntu

## 0.1.1 - 25/02/2016

### Fixed

* Switched from deprecated 'categories' to 'galaxy_tags' in role meta

## 0.1.0 - 25/02/2016

### Added

* Initial version
