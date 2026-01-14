# POM_SauceLabs_Playwright_TypeScript

This project demonstrates automation testing using Playwright with TypeScript, implementing the Page Object Model (POM) pattern for [Sauce Demo](https://www.saucedemo.com/) website. The project includes automated testing of the complete e-commerce workflow from login to order completion.

## 🚀 Features

- **Page Object Model (POM) implementation** - Clean, maintainable test code structure
- **TypeScript support** - Type-safe test automation
- **Parallel test execution** - Fast test runs
- **Cross-browser testing** - Tests run on Chromium, Firefox, and WebKit
- **Mobile testing** - Supports mobile viewports (Chrome Mobile, Safari Mobile)
- **GitHub Actions CI/CD** - Automated testing on every push and pull request
- **Comprehensive test coverage** - Tests for complete e-commerce workflow and error handling
- **HTML Test Reports** - Beautiful, interactive test reports

## 📋 Project Overview

This project automates the testing of the SauceDemo e-commerce website. It tests the complete user journey:

1. **Login** - Validates user authentication
2. **Product Selection** - Adds products to cart
3. **Cart Management** - Verifies cart contents
4. **Checkout Process** - Fills customer information
5. **Order Review** - Verifies order details
6. **Order Completion** - Confirms successful order

The framework uses the **Page Object Model (POM)** design pattern, which provides:
- **Reusability** - Page objects can be reused across multiple tests
- **Maintainability** - Changes to UI only require updates in page objects
- **Readability** - Tests are written in plain language, easy to understand
- **Scalability** - Easy to add new tests and page objects

## 🛠️ Prerequisites

- **Node.js** (v18 or higher recommended)
- **npm** (comes with Node.js) or **yarn**
- **Git** (for version control)

## 📦 Installation & Setup

### Local Setup

1. **Clone or navigate to the repository:**
   ```bash
   cd POM_SauceLabs
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Install Playwright browsers:**
   ```bash
   npx playwright install
   ```

### First Run

After installation, you can run tests immediately:
```bash
npm test
```

## 🏃‍♂️ Running Tests

### Basic Commands

**Run all tests:**
```bash
npm test
```

**Run tests in headed mode (see browser):**
```bash
npm run test:headed
```

**Run tests in UI mode (interactive):**
```bash
npm run test:ui
```

**Run tests in debug mode:**
```bash
npm run test:debug
```

### Browser-Specific Tests

**Run tests in Chromium only:**
```bash
npm run test:chromium
```

**Run tests in Firefox only:**
```bash
npm run test:firefox
```

**Run tests in WebKit (Safari) only:**
```bash
npm run test:webkit
```

### Advanced Options

**Run specific test file:**
```bash
npx playwright test tests/saucedemo.spec.ts
```

**Run tests matching a pattern:**
```bash
npx playwright test --grep "login"
```

**Run tests in multiple browsers:**
```bash
npx playwright test --project=chromium --project=firefox
```

## 📊 Viewing Test Reports

After running tests, view the HTML report:
```bash
npm run test:report
```

This opens an interactive HTML report showing:
- Test execution status
- Screenshots on failure
- Video recordings (on failure)
- Test traces
- Execution timeline

## 📁 Project Structure

```
POM_SauceLabs/
├── .github/
│   └── workflows/
│       └── playwright.yml    # GitHub Actions CI/CD workflow
├── src/
│   ├── pages/                # Page Object Model classes
│   │   ├── BasePage.ts       # Base page with common methods
│   │   ├── LoginPage.ts      # Login page object
│   │   ├── ProductsPage.ts   # Products listing page
│   │   ├── CartPage.ts       # Shopping cart page
│   │   ├── CheckoutPage.ts   # Checkout base page
│   │   ├── CheckoutStepOnePage.ts  # Customer info form
│   │   ├── CheckoutStepTwoPage.ts  # Order review page
│   │   └── CheckoutCompletePage.ts # Order confirmation
│   └── utils/
│       ├── Constants.ts      # Test constants (URLs, credentials)
│       └── TestData.ts       # Test data utilities
├── tests/
│   ├── saucedemo.spec.ts     # Main e-commerce workflow tests
│   └── framework-demo.spec.ts # Framework demonstration tests
├── playwright.config.ts      # Playwright configuration
├── tsconfig.json             # TypeScript configuration
├── package.json              # Project dependencies and scripts
└── README.md                 # Project documentation
```

## 🔧 Key Components

### Page Objects (`src/pages/`)
Each page of the application has a corresponding page object class:
- **BasePage**: Contains common methods used by all page objects
- **LoginPage**: Handles login functionality
- **ProductsPage**: Manages product browsing and cart actions
- **CartPage**: Handles cart operations
- **CheckoutStepOnePage**: Manages customer information form
- **CheckoutStepTwoPage**: Handles order review
- **CheckoutCompletePage**: Verifies order completion

### Test Files (`tests/`)
- **saucedemo.spec.ts**: Comprehensive test suite covering the complete e-commerce workflow
  - Complete workflow test (login → add to cart → checkout → complete order)
  - Individual component tests
  - Negative test cases (error handling)

### Configuration
- **playwright.config.ts**: Configured for cross-browser testing, parallel execution, and CI/CD
- **tsconfig.json**: TypeScript compiler settings with path aliases

## 🚀 GitHub Setup & Deployment

### Step 1: Initialize Git Repository

If you haven't already initialized git:

```bash
git init
```

### Step 2: Add All Files to Git

```bash
git add .
```

### Step 3: Create Initial Commit

```bash
git commit -m "Initial commit: Playwright TypeScript POM framework"
```

### Step 4: Create GitHub Repository

1. Go to [GitHub](https://github.com) and sign in
2. Click the **"+"** icon in the top right → **"New repository"**
3. Enter a repository name (e.g., `POM_SauceLabs_Playwright`)
4. Choose **Public** or **Private**
5. **DO NOT** initialize with README, .gitignore, or license (we already have these)
6. Click **"Create repository"**

### Step 5: Connect Local Repository to GitHub

```bash
# Replace <your-username> and <repository-name> with your actual GitHub username and repo name
git remote add origin https://github.com/<your-username>/<repository-name>.git
git branch -M main
git push -u origin main
```

**Example:**
```bash
git remote add origin https://github.com/yourusername/POM_SauceLabs_Playwright.git
git branch -M main
git push -u origin main
```

### Step 6: Verify GitHub Actions

Once pushed, GitHub Actions will automatically:
- ✅ Run tests on every push to `main`, `master`, or `develop` branches
- ✅ Run tests on every pull request
- ✅ Test on Chromium, Firefox, and WebKit browsers
- ✅ Upload test reports as artifacts

**To view GitHub Actions:**
1. Go to your repository on GitHub
2. Click on the **"Actions"** tab
3. You'll see workflow runs with test results

**To view test reports:**
1. Click on a workflow run
2. Scroll down to **"Artifacts"** section
3. Download `playwright-report` to view the HTML report

## 🔄 GitHub Actions Workflow

The project includes a pre-configured GitHub Actions workflow (`.github/workflows/playwright.yml`) that:

- **Triggers automatically** on:
  - Push to `main`, `master`, or `develop` branches
  - Pull requests to these branches
  - Manual workflow dispatch (via GitHub UI)

- **Runs tests** in parallel on:
  - Chromium (Chrome/Edge)
  - Firefox
  - WebKit (Safari)

- **Generates artifacts**:
  - Test reports (HTML format)
  - Screenshots on failures
  - Video recordings on failures
  - Test traces for debugging

## 📝 Making Changes & Pushing Updates

### Workflow:

1. **Make your changes** to code or tests

2. **Stage your changes:**
   ```bash
   git add .
   ```

3. **Commit your changes:**
   ```bash
   git commit -m "Your descriptive commit message"
   ```

4. **Push to GitHub:**
   ```bash
   git push origin main
   ```

GitHub Actions will automatically run tests on your push!

## 🐛 Troubleshooting

### Tests fail locally?

1. **Reinstall dependencies:**
   ```bash
   rm -rf node_modules package-lock.json
   npm install
   npx playwright install
   ```

2. **Check Playwright installation:**
   ```bash
   npx playwright --version
   ```

3. **Run tests in headed mode to see what's happening:**
   ```bash
   npm run test:headed
   ```

### GitHub Actions failing?

1. Check the Actions tab for detailed error logs
2. Ensure `package-lock.json` is committed (it should be)
3. Verify Node.js version in workflow file matches your local setup

### Can't push to GitHub?

1. **Check remote URL:**
   ```bash
   git remote -v
   ```

2. **Update remote if needed:**
   ```bash
   git remote set-url origin https://github.com/<username>/<repo>.git
   ```

3. **Authentication issues?** Use GitHub CLI or SSH keys:
   ```bash
   # Using GitHub CLI
   gh auth login
   
   # Or use SSH (recommended)
   git remote set-url origin git@github.com:<username>/<repo>.git
   ```

