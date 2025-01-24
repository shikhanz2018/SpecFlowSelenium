SpecFlow Automation Testing

This repository contains an automation testing framework for web applications using 
**SpecFlow**, **Selenium WebDriver**, and **C#**. SpecFlow is a popular framework for 
behavior-driven development (BDD), allowing you to write tests in natural language (Gherkin) 
and execute them with C# code.

Prerequisites

To run the tests in this repository, you'll need to have the following tools installed on your system:

- **.NET SDK** (for building and running the tests)
- **Visual Studio** or **Visual Studio Code** (for editing and running tests)
- **Selenium WebDriver** (for web automation)
- **SpecFlow** (for BDD testing)
- **ChromeDriver** (or other browser drivers for Selenium)

Installation

Follow these steps to set up the project locally:

### 1. Clone the Repository
Clone the repository to your local machine using the following command:

```bash
git clone https://github.com/username/repository-name.git
```

### 2. Install NuGet Packages
In your Visual Studio project, open the **NuGet Package Manager** and install the following packages:

- **SpecFlow**
- **SpecFlow.NUnit** (or another test framework like MSTest or xUnit)
- **Selenium.WebDriver**
- **Selenium.Chrome.WebDriver** (or other browser drivers based on your browser)

You can install these packages using the **Package Manager Console**:

```bash
Install-Package SpecFlow
Install-Package SpecFlow.NUnit
Install-Package Selenium.WebDriver
Install-Package Selenium.Chrome.WebDriver
```

### 3. Set Up WebDriver
Make sure you have the appropriate **ChromeDriver** (or the driver for your browser) installed and that it matches the version of your browser. You can download **ChromeDriver** from [here](https://sites.google.com/a/chromium.org/chromedriver/).

Project Structure

The project is organized as follows:

```
/SpecFlowSelenium
|-- /Features                   # Gherkin feature files
|-- /StepDefinitions            # C# code for step definitions
|-- /Pages                      # Page Object Model classes for encapsulating interactions
|-- /Hooks                      # Before and After hooks for managing WebDriver
|-- /Utilities                  # Utility classes (e.g., WebDriverManager)
|-- /bin                        # Compiled binaries (auto-generated)
|-- /obj                        # Intermediate build files
```

### Key Components

- **Feature Files**: Located in the `/Features` directory, these files describe the behavior of the application in Gherkin syntax.
- **Step Definitions**: Located in the `/StepDefinitions` directory, these files contain the C# code that corresponds to the steps written in the feature files.
- **Page Object Model (POM)**: The `/Pages` directory contains the Page Object Model classes that represent the web pages in the application under test.
- **Hooks**: Located in the `/Hooks` directory, these files define actions that should be performed before or after each scenario, such as initializing and disposing of the WebDriver.

Running Tests

To run the tests, you can use **Visual Studio Test Explorer** or the **dotnet CLI**.

### Using Visual Studio
1. Open the project in Visual Studio.
2. Build the solution.
3. Open the **Test Explorer** and run the tests.

### Using dotnet CLI
To run the tests via the command line, navigate to the project folder and use the following command:

```bash
dotnet test
```

This will build and run all the tests in the project.

Writing Tests

SpecFlow tests are written in **Gherkin** syntax. Here's an example feature file:

```gherkin
Feature: Login functionality

  Scenario: Valid user can log in
    Given I open the login page
    When I enter a valid username and password
    Then I should see the dashboard
```

For each scenario in the feature file, you'll need to create corresponding step definitions in C#.

Example Step Definitions

Here’s an example of step definitions in C#:

```csharp
[Binding]
public class LoginSteps
{
    private readonly IWebDriver _driver;

    public LoginSteps(IWebDriver driver)
    {
        _driver = driver;
    }

    [Given(@"I open the login page")]
    public void GivenIOpenTheLoginPage()
    {
        _driver.Navigate().GoToUrl("https://example.com/login");
    }

    [When(@"I enter a valid username and password")]
    public void WhenIEnterAValidUsernameAndPassword()
    {
        _driver.FindElement(By.Id("username")).SendKeys("validUser");
        _driver.FindElement(By.Id("password")).SendKeys("validPassword");
        _driver.FindElement(By.Id("loginButton")).Click();
    }

    [Then(@"I should see the dashboard")]
    public void ThenIShouldSeeTheDashboard()
    {
        Assert.True(_driver.FindElement(By.Id("dashboard")).Displayed);
    }
}
```

Contributing

Feel free to fork this repository and submit pull requests. If you have any bug reports or feature requests, please open an issue in the Issues section.

License

This project is licensed under the MIT License.

