Auto_Amaze: Cleartrip Automation Framework
This project is an automation framework designed to handle the Cleartrip Flight Search use case. It focuses on handling dynamic web elements, asynchronous data loading, and popups using a resilient Page Object Model (POM) architecture.

🛠 Tech Stack
Language: Java 21

Automation Tool: Selenium WebDriver (v4.21.0)

Test Framework: TestNG (v7.9.0)

Build Tool: Maven

🏗 Framework Architecture
The framework follows the Page Object Model (POM) pattern to ensure high maintainability and code reusability.

Key Components
base/BaseTest.java: Centralized configuration class. It manages the WebDriver lifecycle (setup/teardown), handles Chrome browser options (incognito mode, disabling automation flags), and maximizes window settings to ensure a consistent test environment.

utils/WaitUtils.java: A custom wrapper for explicit waits. It abstracts complex Selenium WebDriverWait logic into reusable methods, including:

waitForClickable: Ensures elements are interactable before clicks.

waitForPageStability: Uses document.readyState via JavaScript to verify page load completion.

Custom retry and sleep handling for high-latency dynamic elements.

pages/: Contains page-specific classes (HomePage, SearchResultsPage) that encapsulate locators and business logic.

tests/: Contains test scripts (e.g., FlightSearchTest) that extend BaseTest and execute business workflows.

🚀 Key Features
Dynamic Popup Handling: Uses a combination of JavascriptExecutor and explicit waits to identify and close intrusive marketing popups before test execution.

JS Fallback Mechanism: When standard Selenium .click() actions fail due to overlays or blocking elements, the framework defaults to JavascriptExecutor to ensure interactions are registered.

Resilient Locators: Uses relative and text-based XPaths to interact with the highly dynamic UI of the Cleartrip website.

📋 Prerequisites
Java JDK 21 installed and configured.

Maven installed.

Chrome browser installed.

💻 How to Run
Clone the repository.

Navigate to the project root.

Run tests via Maven:

Bash
mvn test
Custom Execution: To run specific test suites, you can invoke the testng.xml file via the command line or your IDE's TestNG plugin.

📂 Project Structure
Plaintext
Auto_Amaze/
├── src/test/java/
│   ├── base/           # BaseTest.java (Setup & Configuration)
│   ├── pages/          # HomePage.java, SearchResultsPage.java (Page Classes)
│   ├── tests/          # FlightSearchTest.java (Test Scripts)
│   └── utils/          # WaitUtils.java (Custom Wait Utilities)
├── pom.xml             # Maven dependencies
└── testng.xml          # Test Suite Configuration
