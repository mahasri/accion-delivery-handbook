# ESLint

ESLint is an essential tool in React to maintain code quality, consistency, and reduce potential bugs in the application.

## Overview

ESLint is a powerful static code analysis tool that helps identify and fix problems in JavaScript code. It enforces coding standards and best practices, making it easier to maintain large codebases and collaborate with teams.

## Capabilities

ESLint can:

### 1. Error Detection
- Search for syntax errors, potential bugs, and issues in the code before they become problematic
- Find issues like unused variables, unreachable code, or console statements that are overlooked during development

### 2. Code Style Enforcement
- Enforce consistent code style across the entire project and team, making the code easier to read
- Define rules for indentation, semicolons, quotes, line length, and other stylistic elements

### 3. React-Specific Best Practices
- Adopt plugins like `eslint-plugin-react` and `eslint-plugin-react-hooks` to enforce best practices specifically for React applications
- Use destructuring props, avoid inline styles, and manage dependencies properly

### 4. Real-Time Feedback
- Integrate with code editors like Visual Studio Code, providing real-time linting feedback
- Make it easier to fix issues immediately, reducing the need to run manual checks frequently

### 5. Automatic Code Fixing
- Automate fixing of certain issues (e.g., formatting, simple stylistic errors) with the `--fix` option
- Save time and ensure consistent formatting without manual intervention

### 6. Team Collaboration
- Improve team collaboration when working with a team by ensuring everyone adheres to the same standards
- Make code reviews and collaboration smoother

### 7. Tool Integration
- Integrate with other tools (e.g., Prettier) for code formatting while ESLint focuses on code quality and potential errors
- Configure `eslint-config-prettier` to make ESLint and Prettier work together without conflicts
- Ensure code is free of errors

## Key Features

### 1. Customizable Rules
- Configure rules based on project requirements
- Create custom rules for specific coding patterns
- Use severity levels: error, warning, or off

### 2. Plugin Ecosystem
- Extensive plugin ecosystem for various frameworks and libraries
- React-specific plugins for component development
- Hook-specific rules for proper React Hooks usage

### 3. Configuration Options
- Multiple configuration formats: `.eslintrc.json`, `.eslintrc.js`, `package.json`
- Environment-specific configurations
- Shareable configuration presets

### 4. IDE Integration
- Built-in support for popular IDEs
- Real-time error highlighting
- Quick-fix suggestions

## Installation

### Basic Installation

```bash
npm install eslint --save-dev
```

### Initialize Configuration

```bash
npx eslint --init
```

### Install React Plugins

```bash
npm install eslint-plugin-react eslint-plugin-react-hooks --save-dev
```

## Configuration

### Basic `.eslintrc.json` Configuration

```json
{
  "env": {
    "browser": true,
    "es2021": true,
    "node": true
  },
  "extends": [
    "eslint:recommended",
    "plugin:react/recommended",
    "plugin:react-hooks/recommended"
  ],
  "parserOptions": {
    "ecmaFeatures": {
      "jsx": true
    },
    "ecmaVersion": 12,
    "sourceType": "module"
  },
  "plugins": [
    "react",
    "react-hooks"
  ],
  "rules": {
    "indent": ["error", 2],
    "quotes": ["error", "single"],
    "semi": ["error", "always"],
    "no-unused-vars": "warn",
    "no-console": "warn",
    "react/prop-types": "off"
  }
}
```

### Integration with Prettier

```bash
npm install eslint-config-prettier eslint-plugin-prettier --save-dev
```

Update `.eslintrc.json`:

```json
{
  "extends": [
    "eslint:recommended",
    "plugin:react/recommended",
    "plugin:prettier/recommended"
  ]
}
```

## Usage

### Command Line

```bash
# Lint all files in src directory
npx eslint src/

# Lint specific file
npx eslint src/App.js

# Auto-fix issues
npx eslint src/ --fix

# Lint and output to file
npx eslint src/ -o eslint-report.html -f html
```

### VS Code Integration

1. Install ESLint extension from VS Code marketplace
2. Add to `settings.json`:

```json
{
  "eslint.enable": true,
  "eslint.autoFixOnSave": true,
  "eslint.validate": [
    "javascript",
    "javascriptreact",
    "typescript",
    "typescriptreact"
  ]
}
```

## Common Rules for React

### Recommended React Rules

```json
{
  "rules": {
    "react/jsx-uses-react": "error",
    "react/jsx-uses-vars": "error",
    "react/jsx-key": "error",
    "react/no-unknown-property": "error",
    "react/no-deprecated": "warn",
    "react/jsx-no-duplicate-props": "error",
    "react/jsx-no-undef": "error",
    "react/jsx-pascal-case": "error"
  }
}
```

### React Hooks Rules

```json
{
  "rules": {
    "react-hooks/rules-of-hooks": "error",
    "react-hooks/exhaustive-deps": "warn"
  }
}
```

## Best Practices

### 1. Use Consistent Configuration
- Maintain a single ESLint configuration across the project
- Use shareable configs for consistency across multiple projects
- Version control your ESLint configuration

### 2. Integrate with CI/CD
- Add ESLint checks to your CI/CD pipeline
- Fail builds on ESLint errors
- Generate and archive ESLint reports

```yaml
# Example GitHub Actions workflow
- name: Run ESLint
  run: npx eslint . --ext .js,.jsx,.ts,.tsx
```

### 3. Regular Updates
- Keep ESLint and plugins updated
- Review and update rules periodically
- Test configuration changes in development first

### 4. Team Guidelines
- Document project-specific ESLint rules
- Conduct team reviews of ESLint configuration
- Provide training on ESLint usage and best practices

### 5. Performance Optimization
- Use `.eslintignore` to exclude unnecessary files
- Optimize file patterns in scripts
- Consider using ESLint cache for faster subsequent runs

```bash
npx eslint . --cache
```

## Common Issues and Solutions

### 1. Parsing Errors
**Issue**: ESLint fails to parse modern JavaScript syntax

**Solution**: Update parser options in configuration

```json
{
  "parserOptions": {
    "ecmaVersion": "latest",
    "sourceType": "module"
  }
}
```

### 2. Plugin Conflicts
**Issue**: Conflicting rules between plugins

**Solution**: Use `eslint-config-prettier` to disable conflicting rules

### 3. Performance Issues
**Issue**: ESLint runs slowly on large codebases

**Solutions**:
- Enable caching: `--cache`
- Limit file scope
- Use `.eslintignore` effectively

## Integration Examples

### Package.json Scripts

```json
{
  "scripts": {
    "lint": "eslint src/",
    "lint:fix": "eslint src/ --fix",
    "lint:report": "eslint src/ -f html -o reports/eslint-report.html"
  }
}
```

### Pre-commit Hook with Husky

```bash
npm install husky lint-staged --save-dev
```

Add to `package.json`:

```json
{
  "husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
  "lint-staged": {
    "*.{js,jsx}": ["eslint --fix", "git add"]
  }
}
```

## Resources

### Official Documentation
- [ESLint Official Documentation](https://eslint.org/docs/latest/)
- [ESLint Rules Reference](https://eslint.org/docs/rules/)

### React-Specific
- [eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react)
- [eslint-plugin-react-hooks](https://www.npmjs.com/package/eslint-plugin-react-hooks)

### Configuration Presets
- [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)
- [Standard JS](https://standardjs.com/)
- [Google JavaScript Style Guide](https://google.github.io/styleguide/jsguide.html)

## Related Topics

- [Development Best Practices](../development.md)
- [Code Review Guidelines](../../appendix/sdlc-tools/code-review.md)
- [SDLC Tools Overview](index.md)

---

*For any queries related to ESLint configuration at Accion Labs, contact the development team or write to pmo@accionlabs.com*
