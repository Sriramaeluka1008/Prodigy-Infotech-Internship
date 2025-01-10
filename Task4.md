# TASK 4: Cross-Browser Testing with BrowserStack

Run automated tests across multiple browsers and devices using BrowserStack to ensure compatibility.

## Requirements
- Use BrowserStack’s Selenium Grid to run your test scripts across different browsers and devices.
- Test a login or form submission page across Chrome, Firefox, Safari, and Edge.
- Document any issues or inconsistencies across browsers.

## Test Code

```python
import pytest
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys

@pytest.fixture(scope="class")
def browserstack_driver(request):
    """
    Fixture to initialize a BrowserStack session.
    """
    desired_cap = {
        'browser': request.param['browser'],
        'browser_version': request.param['browser_version'],
        'os': request.param['os'],
        'os_version': request.param['os_version'],
        'resolution': request.param['resolution'],
        'name': request.node.name,
        'build': 'BrowserStack Build',
        'project': 'BrowserStack Project',
        'browserstack.user': "YOUR_BROWSERSTACK_USERNAME",
        'browserstack.key': "YOUR_BROWSERSTACK_ACCESS_KEY"
    }

    driver = webdriver.Remote(
        command_executor="https://hub-cloud.browserstack.com/wd/hub",
        desired_capabilities=desired_cap
    )

    yield driver
    driver.quit()

@pytest.mark.parametrize('browserstack', [
    {'browser': 'Chrome', 'browser_version': 'latest', 'os': 'Windows', 'os_version': '11', 'resolution': '1024x768'},
    {'browser': 'Firefox', 'browser_version': 'latest', 'os': 'Windows', 'os_version': '11', 'resolution': '1024x768'},
    {'browser': 'Safari', 'browser_version': 'latest', 'os': 'macOS', 'os_version': 'Ventura', 'resolution': '1280x800'},
    {'browser': 'Edge', 'browser_version': 'latest', 'os': 'Windows', 'os_version': '11', 'resolution': '1024x768'}
], indirect=True)
def test_login(browserstack_driver):
    """
    Test login functionality.
    """
    driver = browserstack_driver
    driver.get("YOUR_TEST_PAGE_URL") 

    # --- Login Logic ---
    # 1. Locate username/email field
    # 2. Enter username/email
    # 3. Locate password field
    # 4. Enter password
    # 5. Click login button
    # ---

    # Assert successful login (e.g., check for a welcome message)
    assert "Welcome" in driver.page_source 

if __name__ == "__main__":
    pytest.main()
