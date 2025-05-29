# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.0] - 2025-05-29

### Added
- Initial release of Setup GitHub User Action
- Configure Git username and email globally
- Optional remote origin URL configuration with GitHub defaults
- Input validation for username and email
- Email format validation using regex
- Automatic token-based authentication for GitHub repositories
- Comprehensive error handling and logging
- Output values for configured username, email, and remote URL
- Support for custom Git providers (GitLab, Bitbucket, etc.)
- Automatic detection of existing Git repositories
- Smart remote origin management (add new or update existing)

### Features
- **Username Configuration**: Set global Git username
- **Email Configuration**: Set global Git email with format validation
- **Remote URL Management**: Configure remote origin with intelligent defaults
- **GitHub Integration**: Automatic GitHub repository URL generation with token auth
- **Cross-Platform Support**: Works on ubuntu-latest, windows-latest, and macos-latest
- **Comprehensive Validation**: Input validation with clear error messages
- **Detailed Logging**: Step-by-step logging with success/error notifications

### Outputs
- `configured-user`: The configured Git username
- `configured-email`: The configured Git email  
- `configured-remote`: The configured Git remote origin URL

## [0.1.0] - 2025-05-29

### Added
- Project initialization
- Basic action structure
- Initial documentation