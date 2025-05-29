# Security Policy

## Supported Versions

We provide security updates for the following versions:

| Version | Supported          |
| ------- | ------------------ |
| 1.x.x   | :white_check_mark: |
| < 1.0   | :x:                |

## Reporting a Vulnerability

We take security seriously. If you discover a security vulnerability, please follow these steps:

### 1. **Do Not** Open a Public Issue

Please do not report security vulnerabilities through public GitHub issues, discussions, or pull requests.

### 2. Report Privately

Send details to: [cruiseomondi90@gmail.com]

Include:
- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Any suggested fixes

### 3. Response Timeline

- **Initial Response**: Within 48 hours
- **Status Update**: Within 7 days
- **Fix Timeline**: Varies based on severity

## Security Best Practices

When using this action:

### Token Security
- Use GitHub's built-in `${{ github.token }}` when possible
- Store custom tokens in GitHub Secrets, never in code
- Use fine-grained personal access tokens with minimal permissions

### Input Validation
- This action validates all inputs
- Email format is verified using regex
- Username and email are required fields

### Remote URL Security
- Default GitHub URLs use token authentication
- Custom remote URLs should use HTTPS
- Avoid embedding credentials in URLs

## Scope

This security policy covers:
- The GitHub Action code (`action.yml`)
- Documentation and examples
- Dependencies and external calls

## Known Considerations

### Git Configuration
- This action sets global Git configuration
- Configuration persists for the duration of the job
- Multiple jobs may need separate configuration

### Token Usage
- Tokens are used for repository authentication
- Tokens are not logged or exposed in outputs
- Default GitHub token has appropriate repository permissions

## Updates

Security updates will be:
- Released as patch versions
- Documented in CHANGELOG.md
- Announced in GitHub Releases

## Contact

For security concerns: [cruiseomondi90@gmail.com]
For general questions: Open a GitHub issue