# Setup git User Action

A git Action to configure Git username and email in your workflows. This action parses and validates user credentials, then sets up the Git configuration globally for subsequent steps in your workflow.

## Features

- ✅ Configures Git username and email globally
- ✅ Sets up Git remote origin URL (defaults to git repository)
- ✅ Input validation with proper error handling
- ✅ Email format validation
- ✅ Automatic git authentication with tokens
- ✅ Configuration verification
- ✅ Detailed logging and notifications
- ✅ Outputs configured values for downstream steps

## Usage

### Basic Usage

```yaml
name: Example Workflow
on: [push]

jobs:
  setup:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup Git User
        uses: jamie-codez/setup-git-user@v1
        with:
          username: 'John Doe'
          email: 'john.doe@example.com'
          
      - name: Make a commit
        run: |
          echo "Test file" > test.txt
          git add test.txt
          git commit -m "Add test file"
```

### Using Outputs

```yaml
- name: Setup Git User
  id: git-setup
  uses: jamie-codez/setup-git-user@v1
  with:
    username: 'John Doe'
    email: 'john.doe@example.com'
    
- name: Display configured user
  run: |
    echo "Configured user: ${{ steps.git-setup.outputs.configured-user }}"
    echo "Configured email: ${{ steps.git-setup.outputs.configured-email }}"
```

### Using Custom Remote URL

```yaml
- name: Setup Git User with Custom Remote
  uses: jamie-codez/setup-git-user@v1
  with:
    username: 'John Doe'
    email: 'john.doe@example.com'
    remote-url: 'https://git.com/myorg/myrepo.git'
    
- name: Setup with GitLab Remote
  uses: jamie-codez/setup-git-user@v1
  with:
    username: 'John Doe'
    email: 'john.doe@example.com'
    remote-url: 'https://gitlab.com/myorg/myrepo.git'
```

### Default git Remote (Automatic)

```yaml
# This will automatically use: https://github.com/{owner}/{repo}.git
# With token authentication if a token is provided
- name: Setup Git User
  uses: jamie-codez/setup-git-user@v1
  with:
    username: 'John Doe'
    email: 'john.doe@example.com'
    # remote-url is optional - defaults to current git repository
```

### Using git Secrets

```yaml
- name: Setup Git User
  uses: jamie-codez/setup-git-user@v1
  with:
    username: ${{ secrets.GIT_USERNAME }}
    email: ${{ secrets.GIT_EMAIL }}
    remote-url: ${{ secrets.GIT_REMOTE_URL }}  # Optional custom remote
    token: ${{ secrets.git_TOKEN }}
```

### Using Actor Information

```yaml
- name: Setup Git User
  uses: jamie-codez/setup-git-user@v1
  with:
    username: ${{ git.actor }}
    email: ${{ git.actor }}@users.noreply.git.com
    # Defaults to: https://x-access-token:{token}@git.com/{owner}/{repo}.git
```

## Inputs

| Input        | Description                                         | Required | Default                              |
|--------------|-----------------------------------------------------|----------|--------------------------------------|
| `username`   | Git username to configure                           | Yes      | -                                    |
| `email`      | Git email to configure (must be valid email format) | Yes      | -                                    |
| `remote-url` | Git remote origin URL                               | No       | `https://git.com/{owner}/{repo}.git` |
| `token`      | git token for authentication                        | No       | `${{ git.token }}`                   |

## Outputs

| Output              | Description                          |
|---------------------|--------------------------------------|
| `configured-user`   | The configured Git username          |
| `configured-email`  | The configured Git email             |
| `configured-remote` | The configured Git remote origin URL |

## Error Handling

The action includes comprehensive error handling:

- Validates that both username and email are provided
- Validates an email format using regex
- Verifies that Git configuration was applied correctly
- Exits with error code 1 if any validation fails

## Examples

### Multiple Jobs with User Setup

```yaml
name: Multi-job Workflow
on: [push]

jobs:
  setup-and-commit:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup Git User
        uses: jamie-codez/setup-git-user@v1
        with:
          username: 'CI Bot'
          email: 'ci-bot@company.com'
          
      - name: Create commit
        run: |
          echo "$(date)" > timestamp.txt
          git add timestamp.txt
          git commit -m "Update timestamp"
          git push

  another-job:
    runs-on: ubuntu-latest
    needs: setup-and-commit
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup Git User
        uses: jamie-codez/setup-git-user@v1
        with:
          username: 'Release Bot'
          email: 'release-bot@company.com'
          
      - name: Tag release
        run: |
          git tag v1.0.0
          git push --tags
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
Please read our [Conduct Guide](./CODE_OF_CONDUCT.md) before participating.

## License

This project is licensed under the MIT License—see the [LICENSE](./LICENSE.md) file for details.