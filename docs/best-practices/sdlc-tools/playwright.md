# Playwright

Playwright is a powerful open-source automation framework that simplifies web application testing with its robust features like cross-browser support, parallel execution, and code generation.

## Overview

Playwright allows automating and testing web pages across multiple browsers - Chromium, Firefox, and WebKit. By following the steps outlined in this guide, you can set up, test, and automate complex workflows efficiently.

!!! note "Accion Implementation"
    At Accion, QA Automation with Playwright is being implemented for Cision, OMC project. For any queries related to Playwright, write to **pmo@accionlabs.com**.

## Software & System Requirements

### Required Software
- **Node.js**: Version 18 or higher
- **IDE**: Visual Studio Code (recommended)

### Supported Operating Systems
- **Windows**: Windows 10+, Windows Server 2016+ or Windows Subsystem for Linux (WSL)
- **macOS**: macOS 13 Ventura, or macOS 14 Sonoma
- **Linux**: 
  - Debian 11, Debian 12
  - Ubuntu 20.04, Ubuntu 22.04, Ubuntu 24.04
  - Supported architectures: x86-64 and arm64

## Getting Started

This section covers setting up Playwright by installing test playwright for QA automation and code generation.

### Installation Methods

Playwright can be installed using either the Command line or VS Code extension.

#### Method 1: Using Command Line

1. **Create a New Node.js Project**

   Create a new directory for the playwright project and navigate to it:

   ```bash
   mkdir my-playwright-project
   cd my-playwright-project
   npm init -y
   ```

   This creates a new Node.js project with a `package.json` file.

2. **Install Playwright**

   Use npm/yarn/pnpm to install playwright:

   ```bash
   npm install playwright
   ```

   Playwright automatically downloads the required browser binaries (Chromium, Firefox, WebKit) during installation.

#### Method 2: Using VS Code Extension

1. Launch VS Code Editor and install Playwright from the marketplace or extensions tab

2. Open the command palette and paste "Install Playwright"

3. Choose the browsers to run the tests (configured in the playwright.config file)

4. Choose GitHub Actions setup to run tests on CI

5. The Playwright UI will show the test explorer with all files in the project

### Configuration

The Playwright Configuration file (`playwright.config.js` or `.ts`) defines the test options:

- Test directory
- Browser settings
- Timeouts
- Base URL
- Parallelism
- Test retries
- Reporters

#### Example Configuration

```javascript
// playwright.config.js
module.exports = {
  use: {
    baseURL: 'https://example.com',
    browserName: 'chromium',
    headless: true,
    viewport: { width: 1280, height: 720 },
  },
  retries: 2, // Retry failed tests
};
```

### Verification

To verify Playwright setup, create and run a test script:

1. Create a sample test script `test.js`:

```javascript
const { chromium } = require('playwright');

(async () => {
  const browser = await chromium.launch();
  const page = await browser.newPage();
  await page.goto('https://example.com');
  console.log(await page.title());
  await browser.close();
})();
```

2. Run the script:

```bash
node test.js
```

If the webpage title is printed in the console, Playwright is set up correctly.

## Writing Tests

Playwright supports writing tests using various programming languages, including TypeScript/JavaScript, Python, .NET, and Java. The examples in this document use TypeScript/JavaScript.

### Basic Test Structure

```javascript
const { test, expect } = require('@playwright/test');

test('example test', async ({ page }) => {
  // Navigate to the page
  await page.goto('https://example.com');
  
  // Interact with elements
  await page.click('button#login');
  await page.fill('input#username', 'user');
  await page.fill('input#password', 'password');
  await page.click('button#submit');
  
  // Assert expected outcomes
  const welcomeMessage = await page.locator('h1').textContent();
  expect(welcomeMessage).toContain('Welcome');
});
```

### Common Actions and Assertions

#### Interactions
- `click()` - Click on elements
- `fill()` - Fill input fields
- `hover()` - Hover over elements
- `type()` - Type text character by character
- `selectOption()` - Select dropdown options
- `check()` / `uncheck()` - Handle checkboxes

#### Assertions
- `expect()` with matchers:
  - `toContainText()` - Check text content
  - `toBeVisible()` - Verify element visibility
  - `toBeEnabled()` - Check if element is enabled
  - `toHaveCount()` - Verify element count
  - `toHaveValue()` - Check input values

## Running Tests

### Command Line Execution

```bash
# Run all tests
npx playwright test

# Run specific test file
npx playwright test example.spec.js

# Run in debug mode
npx playwright test --debug

# Run in headed mode (visible browser)
npx playwright test --headed

# Run specific browser
npx playwright test --project=chromium
npx playwright test --project=firefox
npx playwright test --project=webkit
```

### VS Code Execution

1. Click the Testing icon in the sidebar to view all test cases

2. Hover over a test case and click execute

3. Test results appear in the right panel

### Playwright UI Mode

Run tests with the Playwright UI tool:

```bash
npx playwright test --ui
```

The UI provides:
- Visual test execution
- Step-by-step debugging
- Test results in real-time
- Network activity monitoring

## Code Generation (Codegen)

Playwright's codegen tool simplifies test creation by recording browser actions and generating equivalent code.

### Using Codegen

1. **Start Recording**

   In VS Code, scroll down to Playwright menu and click "Record new"
   
   Or via command line:
   
   ```bash
   npx playwright codegen
   ```

2. **Interact with Application**

   - Enter application URL
   - Perform user interactions (clicks, text input, navigation)
   - Actions are automatically captured as test code

3. **Save Generated Code**

   The generated test cases can be organized into folders to avoid re-running of test cases

### Example Generated Code

```javascript
import { test, expect } from '@playwright/test';

test('test', async ({ page }) => {
  await page.goto('https://example.com/');
  await page.getByLabel('Username').fill('testuser');
  await page.getByLabel('Password').fill('password123');
  await page.getByRole('button', { name: 'Login' }).click();
  await expect(page.getByText('Welcome')).toBeVisible();
});
```

## Test Organization

### Project Structure

```
my-playwright-project/
├── tests/
│   ├── auth/
│   │   ├── login.spec.js
│   │   └── logout.spec.js
│   ├── dashboard/
│   │   └── dashboard.spec.js
│   └── api/
│       └── api-tests.spec.js
├── playwright.config.js
└── package.json
```

### Test Configuration Options

```javascript
// playwright.config.js
module.exports = {
  testDir: './tests',
  timeout: 30000,
  retries: 2,
  workers: 4, // Parallel execution
  
  use: {
    baseURL: 'https://example.com',
    screenshot: 'only-on-failure',
    video: 'retain-on-failure',
    trace: 'on-first-retry',
  },
  
  projects: [
    {
      name: 'chromium',
      use: { browserName: 'chromium' },
    },
    {
      name: 'firefox',
      use: { browserName: 'firefox' },
    },
    {
      name: 'webkit',
      use: { browserName: 'webkit' },
    },
  ],
};
```

## Generating Reports

### Default Reports

By default, Playwright provides a test report after execution:

```bash
npx playwright show-report
```

### Custom Reporters

Configure custom reporters in `playwright.config.js`:

```javascript
module.exports = {
  reporter: [
    ['html', { outputFolder: 'playwright-report' }],
    ['json', { outputFile: 'test-results.json' }],
    ['junit', { outputFile: 'junit-results.xml' }],
  ],
};
```

### Report Types

1. **HTML Report**: Interactive report with screenshots and videos
2. **JSON Report**: Machine-readable format for CI/CD integration
3. **JUnit Report**: Standard format for test result tracking

## Case Study: QA Automation using Playwright

### Scenario

A web application built with:
- **Frontend**: React.js
- **Backend**: GraphQL (GQL) and .NET Core Web API

Required robust QA automation to streamline testing processes.

### Implementation

QA automation was implemented across three layers:

1. **UI Automation**: For validating the frontend built with React.js
2. **GraphQL Automation**: For querying and validating API responses
3. **API Automation**: For testing backend endpoints exposed by the .NET Core Web API

### CI/CD Integration

#### GitHub Actions Setup

GitHub Actions were used to integrate QA automation into the CI/CD pipeline:

**Trigger Methods:**

1. **Manual Execution**
   - Test cases manually triggered in required environments via CI/CD pipeline
   - Results sent to Slack channel to notify the team

2. **Automated Execution on Deployment**
   - When main application is deployed, pipeline automatically triggers key test cases
   - Test results shared via Slack for quick visibility and resolution

#### Example GitHub Actions Workflow

```yaml
name: Playwright Tests

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main ]
  workflow_dispatch:

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'
      
      - name: Install dependencies
        run: npm ci
      
      - name: Install Playwright browsers
        run: npx playwright install --with-deps
      
      - name: Run Playwright tests
        run: npx playwright test
      
      - name: Upload test results
        if: always()
        uses: actions/upload-artifact@v3
        with:
          name: playwright-report
          path: playwright-report/
```

### Custom Configuration

The Playwright config file included:

- Multiple environment support (staging, production)
- Parallel test execution to optimize runtimes
- Custom reporters for detailed logs
- Slack notifications integration
- Environment-specific test data
- Authentication setups

### Outcomes

The implementation achieved:

1. **Faster Feedback Cycles**: During development and deployment
2. **Reduced Manual Testing**: With reliable and repeatable automated tests
3. **Improved Collaboration**: Through team notifications via Slack
4. **Better Quality**: Consistent test coverage across all environments

## Advanced Features

### Network Interception

```javascript
test('intercept API calls', async ({ page }) => {
  // Mock API response
  await page.route('**/api/users', route => {
    route.fulfill({
      status: 200,
      body: JSON.stringify({ users: [] }),
    });
  });
  
  await page.goto('https://example.com');
});
```

### Browser Contexts

```javascript
test('use multiple contexts', async ({ browser }) => {
  // Create isolated browser contexts
  const context1 = await browser.newContext();
  const context2 = await browser.newContext();
  
  const page1 = await context1.newPage();
  const page2 = await context2.newPage();
  
  // Each context has isolated cookies, storage, etc.
});
```

### Visual Regression Testing

```javascript
test('visual comparison', async ({ page }) => {
  await page.goto('https://example.com');
  await expect(page).toHaveScreenshot('homepage.png');
});
```

### Mobile Emulation

```javascript
const { devices } = require('@playwright/test');

test.use({ ...devices['iPhone 13'] });

test('mobile test', async ({ page }) => {
  await page.goto('https://example.com');
  // Test mobile-specific features
});
```

## Pros & Cons

### Pros

1. **Cross-Browser Support**: Supports Chromium, Firefox, and WebKit for comprehensive testing across all major browsers

2. **Multi-Language Support**: Offers SDKs for JavaScript, TypeScript, Python, Java, and C#

3. **Isolation via Browser Contexts**: Allows isolated testing environments within a single browser instance, reducing cross-test interference

4. **Network Interception & Mocking**: Provides powerful network control features for simulating various scenarios

5. **Efficient Automation**: Auto-waiting mechanism reduces flakiness by waiting for elements to reach correct state

6. **Robust Mobile Testing**: Supports mobile emulation for testing on various screen sizes and devices

7. **Parallel Execution**: Reduces test execution time, ideal for CI/CD pipelines

8. **Headless and Headful Modes**: Flexible for different development stages (CI vs debugging)

9. **Code-Based Framework**: Supports web-based applications with comprehensive code-based approach

### Cons

1. **Resource Intensive**: Can be resource-heavy when running multiple browser instances simultaneously

2. **Limited Application Support**: Does not support mobile applications, desktop applications, or low/no-code solutions

3. **Learning Curve**: New users may face challenges due to extensive feature set and configuration options

4. **Limited Built-in Integrations**: Fewer out-of-the-box integrations compared to tools like Cypress

5. **Debugging Complexity**: Debugging headless tests can be challenging, though tools are provided

6. **Larger Installation Size**: Includes multiple browser binaries, increasing disk usage and setup time

7. **Smaller Ecosystem**: Community and ecosystem are smaller compared to established tools like Selenium

8. **Browser Compatibility Issues**: Some advanced features may differ slightly between browsers

9. **Maintenance Overhead**: Keeping up with updates and managing browser versions adds maintenance effort

## Best Practices

### 1. Test Organization
- Group related tests in folders
- Use descriptive test names
- Maintain consistent naming conventions

### 2. Page Object Model
```javascript
// pages/LoginPage.js
class LoginPage {
  constructor(page) {
    this.page = page;
    this.usernameInput = page.locator('#username');
    this.passwordInput = page.locator('#password');
    this.loginButton = page.locator('button[type="submit"]');
  }

  async login(username, password) {
    await this.usernameInput.fill(username);
    await this.passwordInput.fill(password);
    await this.loginButton.click();
  }
}

module.exports = { LoginPage };
```

### 3. Test Data Management
- Externalize test data
- Use fixtures for test setup
- Maintain separate data for different environments

### 4. Error Handling
```javascript
test('handle errors gracefully', async ({ page }) => {
  try {
    await page.goto('https://example.com');
    await page.click('button#submit', { timeout: 5000 });
  } catch (error) {
    console.error('Test failed:', error);
    throw error;
  }
});
```

### 5. Continuous Maintenance
- Regular updates of Playwright and dependencies
- Review and refactor tests periodically
- Monitor test execution times
- Remove flaky tests or stabilize them

## Troubleshooting

### Common Issues

**Issue**: Browser download fails during installation

**Solution**: 
```bash
PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD=1 npm install playwright
npx playwright install chromium
```

**Issue**: Tests timeout frequently

**Solution**: Increase timeout in configuration
```javascript
module.exports = {
  timeout: 60000, // 60 seconds
  use: {
    actionTimeout: 10000,
    navigationTimeout: 30000,
  },
};
```

**Issue**: Element not found

**Solution**: Use more specific locators or wait for element
```javascript
await page.waitForSelector('#element-id');
const element = await page.locator('#element-id');
```

## Resources

### Official Documentation
- **Node.js**: [Installation | Playwright](https://playwright.dev/docs/intro)
- **Python**: [Installation | Playwright Python](https://playwright.dev/python/docs/intro)
- **Java**: [Installation | Playwright Java](https://playwright.dev/java/docs/intro)

### Additional Resources
- **Docker Support**: [Docker | Playwright](https://playwright.dev/docs/docker)
- **VS Code Testing**: [Visual Studio Marketplace: Playwright](https://marketplace.visualstudio.com/items?itemName=ms-playwright.playwright)
- **Debugging**: [Debugging in Visual Studio Code](https://playwright.dev/docs/debug)
- **Cheat Sheet**: [Playwright for QA Automation | Cheat Sheet](https://playwright.dev/docs/best-practices)

### AI-Powered Testing
- [Zerosteps: Auto Playwright with AI](https://zerostep.com/) - Transforming Playwright Tests with AI

### Demo and Training
- Demo Recording links available from PMO team
- Contact: **pmo@accionlabs.com**

## Related Topics

- [QA Best Practices](../qa-best-practices.md)
- [Testing & QA Process](../testing-qa-process.md)
- [Development Best Practices](../development.md)
- [CI/CD Integration](../../appendix/sdlc-tools/deployment.md)

---

*For queries related to Playwright implementation at Accion Labs, contact the QA team or write to pmo@accionlabs.com*
