
# TASK 3: Automated Login Test for a Web Application

Write a test suite in a library of your choice that automates testing login functionality on the given website. You may use other websites too for this task. You have to include positive test cases (valid credentials) and negative cases (invalid credentials, empty fields).

## Test Code

```python
import pytest
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys

# Replace with the actual URL of the website
BASE_URL = "https://www.example.com"

# Replace with the actual username and password fields
USERNAME_FIELD = "username"
PASSWORD_FIELD = "password"

# Replace with the actual login button locator
LOGIN_BUTTON = "login_button"

# Positive test cases with valid credentials
@pytest.mark.parametrize("username, password", [
    ("valid_user1", "valid_password1"),
    ("valid_user2", "valid_password2")
])
def test_login_success(username, password):
    driver = webdriver.Chrome()  # Replace with your preferred driver
    driver.get(BASE_URL)

    # Locate and enter username
    username_field = driver.find_element(By.ID, USERNAME_FIELD)
    username_field.send_keys(username)

    # Locate and enter password
    password_field = driver.find_element(By.ID, PASSWORD_FIELD)
    password_field.send_keys(password)

    # Click the login button
    login_button = driver.find_element(By.ID, LOGIN_BUTTON)
    login_button.click()

    # Assert successful login (e.g., check for a welcome message)
    assert "Welcome" in driver.page_source

    driver.quit()

# Negative test cases with invalid credentials
@pytest.mark.parametrize("username, password, expected_error", [
    ("", "", "Please enter both username and password."),
    ("invalid_user", "invalid_password", "Invalid credentials."),
    ("valid_user", "", "Please enter password."),
    ("", "valid_password", "Please enter username.")
])
def test_login_failure(username, password, expected_error):
    driver = webdriver.Chrome()
    driver.get(BASE_URL)

    # Enter username and password
    username_field = driver.find_element(By.ID, USERNAME_FIELD)
    username_field.send_keys(username)
    password_field = driver.find_element(By.ID, PASSWORD_FIELD)
    password_field.send_keys(password)

    # Click the login button
    login_button = driver.find_element(By.ID, LOGIN_BUTTON)
    login_button.click()

    # Assert the error message
    assert expected_error in driver.page_source

    driver.quit()

```

## Explanation

### 1. Import Necessary Libraries
- **pytest**: Test framework for writing and running tests.
- **webdriver** from **selenium**: For browser interaction.
- **By** and **Keys** from **selenium.webdriver.common**: For element locating and key actions.

### 2. Define Constants
- **BASE_URL**: URL of the website.
- **USERNAME_FIELD**: ID or other locator of the username field.
- **PASSWORD_FIELD**: ID or other locator of the password field.
- **LOGIN_BUTTON**: ID or other locator of the login button.

### 3. Positive Test Cases
- Use the `@pytest.mark.parametrize` decorator to test with multiple sets of valid credentials.
- Each test case:
  - Creates a webdriver instance.
  - Navigates to the website.
  - Locates and enters username and password.
  - Clicks the login button.
  - Asserts successful login by checking for a welcome message or any other indicator.
  - Closes the browser.

### 4. Negative Test Cases
- Use the `@pytest.mark.parametrize` decorator to test with various invalid credentials and empty fields.
- Each test case:
  - Creates a webdriver instance.
  - Navigates to the website.
  - Enters username and password (or empty fields).
  - Clicks the login button.
  - Asserts the expected error message on the page.
  - Closes the browser.

## To Run the Tests
1. Save the code as a Python file (e.g., `test_login.py`).
2. Open a terminal or command prompt.
3. Navigate to the directory where you saved the file.
4. Run the command:
   ```bash
   pytest test_login.py


