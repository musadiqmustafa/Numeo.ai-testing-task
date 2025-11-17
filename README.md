# Numeo.ai Testing Task - E2E Test Automation Framework

## 🎯 Assessment Objective
This project demonstrates the ability to design a robust test automation foundation for a web product using modern tooling and CI/CD workflow best practices.

## 🌐 Target Application
**URL**: [https://ovcharski.com/shop/](https://ovcharski.com/shop/)  
**Type**: E-commerce platform built with WooCommerce  
**Key Features**: User authentication, product catalog, shopping cart, checkout process, user profiles

## 🏗️ Technical Solution

### Framework & Technologies
- **Test Framework**: Playwright with TypeScript
- **Design Pattern**: Page Object Model (POM)
- **CI/CD**: GitHub Actions
- **Reporting**: HTML reports with artifacts
- **Data Management**: Faker.js for dynamic test data
- **Accessibility**: Axe-core integration

### Architecture Overview
```
playwright-e2e/
├── pages/              # Page Object Model classes
├── tests/
│   ├── e2e/           # End-to-end test scenarios
│   ├── api/           # API test scenarios (placeholder)
│   └── ui/            # UI component tests
├── assets/            # Test data and images
├── .github/workflows/ # CI/CD pipeline configuration
└── playwright.config.ts
```

## 🧪 Automated Tests Implemented

### 1. Critical User Flows (End-to-End Tests)

#### Authentication & User Management
- **User Registration** (`register.spec.ts`)
  - Valid registration with all fields
  - Invalid scenarios (existing username, weak password, invalid email)
  - Empty required field validation
- **User Login** (`login-positive.spec.ts`, `login-negative.spec.ts`)
  - Successful authentication flow
  - Invalid credential handling
  - Error message validation

#### E-commerce Core Features
- **Product Search** (`search.spec.ts`)
  - Search by product name (Shirt, Beanie, Album, etc.)
  - Search by SKU
  - Product navigation and details
- **User Profile Management** (`edit-profile.spec.ts`)
  - Profile information updates
  - Avatar image management
  - Cover image functionality

#### Quality Assurance
- **Accessibility Testing** (`accessibility-scan.spec.ts`)
  - Automated WCAG compliance scanning
  - Homepage accessibility validation
  - Detailed accessibility reporting

### 2. Test Organization & Best Practices

#### Page Object Model Implementation
```typescript
// Example: LoginPage.ts
export default class LoginPage {
    private page: Page;
    
    constructor(page: Page) {
        this.page = page;
    }
    
    async login(username: string, password: string) {
        await this.page.getByLabel('Username or email address *').fill(username);
        await this.page.getByLabel('Password *').fill(password);
        await this.page.getByRole('button', { name: 'Log in' }).click();
    }
}
```

#### Data-Driven Testing
- Dynamic test data generation with Faker.js
- CSV file integration for external test data
- Environment-specific configuration

## 🔄 CI/CD Pipeline (GitHub Actions)

### Pipeline Configuration
**Location**: `.github/workflows/playwright.yml`

### Trigger Events
- Push to main/master branches
- Pull request creation/updates

### Pipeline Features
```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
    - Checkout code
    - Setup Node.js 18
    - Install dependencies
    - Install Playwright browsers
    - Execute test suite
    - Upload test artifacts (reports, screenshots)
```

### Automated Test Execution Workflow
1. **Code Commit/Merge** → GitHub Actions triggered
2. **Environment Setup** → Dependencies and browsers installed
3. **Test Execution** → All tests run in parallel
4. **Artifact Collection** → Reports, screenshots, videos saved
5. **Results** → Pass/fail status reported to GitHub

## 🚀 Getting Started

### Prerequisites
- Node.js 18+
- Git

### Setup & Installation
```bash
# Clone repository
git clone https://github.com/musadiqmustafa/Numeo.ai-testing-task.git
cd Numeo.ai-testing-task

# Install dependencies
npm install

# Install Playwright browsers
npm run test:install
```

### Running Tests
```bash
# Run all tests
npm test

# Run with visible browser
npm run test:headed

# Run specific test
npx playwright test login-positive.spec.ts

# View test report
npm run test:report
```

## 📊 Test Execution & Reporting

### Available Commands
| Command | Purpose |
|---------|---------|
| `npm test` | Execute all tests |
| `npm run test:headed` | Run with visible browser |
| `npm run test:debug` | Debug mode with inspector |
| `npm run test:ui` | Interactive UI mode |
| `npm run test:report` | View HTML reports |

### Reporting Features
- **HTML Reports**: Comprehensive test execution details
- **Screenshots**: Captured on test failures
- **Video Recording**: Full test execution playback
- **Trace Files**: Detailed debugging information
- **Accessibility Reports**: WCAG compliance results

## 🏆 Test Automation Best Practices Demonstrated

### 1. Maintainable Code Architecture
- **Page Object Model**: Separation of concerns
- **TypeScript**: Strong typing for reliability
- **Reusable Components**: Common functionality abstraction

### 2. Comprehensive Test Coverage
- **Happy Path Testing**: Critical user journeys
- **Edge Case Handling**: Error scenarios and validation
- **Accessibility Testing**: WCAG compliance automation

### 3. CI/CD Integration
- **Automated Execution**: Tests run on every commit
- **Artifact Management**: Reports and evidence collection
- **Cross-browser Testing**: Multi-browser validation

### 4. Quality Assurance
- **Parallel Execution**: Optimized test runtime
- **Retry Logic**: Handling flaky test scenarios
- **Environment Isolation**: Clean test state management

## 📈 Test Results & Coverage

### Current Test Suite Metrics
- **Total Test Files**: 6 specification files
- **Test Scenarios**: 15+ individual test cases
- **Coverage Areas**: Authentication, Search, Profile Management, Accessibility
- **Execution Time**: ~60 seconds (parallel execution)
- **Browser Support**: Chromium, Firefox, WebKit ready

### Accessibility Testing Results
- **Tool**: Axe-core integration
- **Standards**: WCAG 2.1 AA compliance
- **Automated Scanning**: Homepage and critical flows
- **Reporting**: Detailed JSON output with remediation guidance

## 🔮 Future Enhancement Opportunities

1. **API Testing Integration**: Backend validation alongside UI tests
2. **Visual Regression Testing**: Screenshot comparison automation
3. **Performance Testing**: Load time and responsiveness validation
4. **Mobile Testing**: Responsive design validation
5. **Cross-environment Testing**: Staging/production validation

---

## 📝 Assessment Summary

This test automation framework demonstrates:

✅ **Modern Tooling**: Playwright + TypeScript + GitHub Actions  
✅ **Best Practices**: Page Object Model, parallel execution, comprehensive reporting  
✅ **CI/CD Integration**: Automated pipeline with artifact management  
✅ **Critical Flow Coverage**: Authentication, search, profile management  
✅ **Quality Focus**: Accessibility testing and error scenario validation  

**Target Application**: E-commerce platform with comprehensive user flows  
**Framework Maturity**: Production-ready with extensible architecture  
**Delivery**: Complete automation solution with CI/CD integration

---

## 🛠️ Technical Implementation Details

### Project Structure
See the complete project structure and implementation files in the repository. Key components include:

- **Page Objects** (`/pages/`): Reusable page interaction classes
- **Test Suites** (`/tests/e2e/`): Comprehensive test scenarios
- **Configuration** (`playwright.config.ts`): Environment and execution settings
- **CI/CD Pipeline** (`.github/workflows/`): Automated testing workflow
- **Documentation**: Comprehensive setup and usage guides

### Assessment Fulfillment
✅ **Chosen Application**: E-commerce platform at ovcharski.com/shop  
✅ **Modern Framework**: Playwright with TypeScript  
✅ **Critical Test Coverage**: Authentication, search, profile management, accessibility  
✅ **CI/CD Integration**: GitHub Actions with automated execution and reporting  
✅ **Best Practices**: Page Object Model, parallel execution, comprehensive documentation