
# HCV Config 01

A configuration management repository that defines file and directory permissions for deployment across servers. This repository is part of the HCV (Host Configuration Versioning) system for managing server configurations.

## Overview

This repository contains configuration files that define how files and directories should be deployed and configured on target servers. It uses a YAML-based configuration format to specify ownership, permissions, and file deployment settings.

## Project Structure

```
hcv-config-01/
├── README.md           # This file
├── renovate.json       # Dependency update configuration
├── .config.yml         # Main configuration file
└── tmp/                # Test files and directories
    ├── testfile01
    ├── testfile02
    └── testdir01/
        └── testfile02
```

## Key Files

### **[.config.yml](.config.yml)**
The main configuration file that defines:
- **Directories**: Specifies directory ownership (user/group) and permissions (mode)
- **Files**: Defines individual file ownership and permissions

Example configuration:
```yaml
---
directories:
  - name: tmp/testdir01
    owner: root
    group: root
    mode: "0755"

files:
  - file: tmp/testfile01
    owner: root
    group: root
    mode: "0755"
```

### **[renovate.json](renovate.json)**
Configuration for [Renovate](https://docs.renovatebot.com/) to automate dependency updates and keep the repository current.

### **[.github/release-drafter.yml](.github/release-drafter.yml)** & **[.github/workflows/release-drafter.yml](.github/workflows/release-drafter.yml)**
Automate GitHub release notes and draft releases using [Release Drafter](https://github.com/release-drafter/release-drafter).

### **tmp/**
Contains example files and directories used for testing the configuration management system. These serve as templates and test cases for the deployment process.

## Usage

### Basic Configuration

1. **Update `.config.yml`** to define your file and directory permissions:
   ```yaml
   directories:
     - name: path/to/directory
       owner: username
       group: groupname
       mode: "0755"

   files:
     - file: path/to/file
       owner: username
       group: groupname
       mode: "0644"
   ```

2. **Test your configuration** using the files in the `tmp/` directory as examples.

### Integration with HCV System

This configuration repository is designed to work with:
- **hcv-deploy-files**: Ansible role for deploying configurations
- **hcv-servers**: Server inventory and deployment specifications

The repository is referenced in server configurations like:
```yaml
- name: Config01
  version: master
  repo: /config/hcv-config-01
```

### Automation Features

- **Automated Releases**: GitHub Actions automatically draft releases
- **Dependency Management**: Renovate keeps dependencies up to date
- **Version Control**: Git-based versioning for configuration changes

## Development

1. Clone the repository
2. Modify `.config.yml` to add or update file/directory configurations
3. Test changes using the example files in `tmp/`
4. Commit and push changes
5. Releases are automatically drafted via GitHub Actions

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly with example configurations
5. Submit a pull request

## License

This project is licensed under copyleft terms.
