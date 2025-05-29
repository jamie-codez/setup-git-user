# Contributing to Setup GitHub User Action

Thank you for considering contributing to this project! We welcome contributions from everyone.

## How to Contribute

### Reporting Issues

If you find a bug or have a suggestion for improvement:

1. Check if the issue already exists in the [Issues](/issues) section
2. If not, create a new issue with:
   - Clear title and description
   - Steps to reproduce (for bugs)
   - Expected vs actual behavior
   - Your environment details (OS, GitHub Actions runner, etc.)

### Submitting Changes

1. **Fork the repository**
   ```bash
   git clone https://github.com/your-username/setup-github-user.git
   cd setup-github-user
   ```

2. **Create a feature branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

3. **Make your changes**
   - Follow the existing code style
   - Add tests if applicable
   - Update documentation as needed

4. **Test your changes**
   - Test the action locally using the test workflow
   - Ensure all existing functionality still works

5. **Commit your changes**
   ```bash
   git add .
   git commit -m "feat: add your feature description"
   ```

6. **Push and create a Pull Request**
   ```bash
   git push origin feature/your-feature-name
   ```

## Development Guidelines

### Code Style

- Use clear, descriptive variable names
- Add comments for complex logic
- Follow shell scripting best practices
- Use proper error handling

### Testing

- Test on multiple operating systems if possible
- Include both positive and negative test cases
- Test with different input combinations
- Verify outputs are correct

### Documentation

- Update README.md for new features
- Add examples for new functionality
- Update CHANGELOG.md following [Keep a Changelog](https://keepachangelog.com/)
- Ensure all inputs/outputs are documented

## Pull Request Process

1. Ensure your PR has a clear title and description
2. Reference any related issues
3. Include test results or screenshots if applicable
4. Update documentation as needed
5. Ensure the action works in the test workflow

## Code of Conduct

- Be respectful and inclusive
- Focus on constructive feedback
- Help others learn and grow
- Follow GitHub's community guidelines

## Questions?

If you have questions about contributing, feel free to:
- Open an issue with the "question" label
- Start a discussion in the repository

Thank you for contributing! 🎉