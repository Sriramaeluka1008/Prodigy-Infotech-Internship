# TASK 5: Automated UI Tests for an E-Commerce Checkout Flow

Automate the checkout process on any e-commerce website using any tool of your choice. Your script should include adding items to the cart, filling out checkout forms, and verifying the success message after purchase.

## Requirements
- Verify each page transition and form validation message.
- Document your script and output, noting any issues encountered during automation.

## Test Code

```python
import pytest
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

# Replace with the actual URL of the e-commerce website
BASE_URL = "https://www.example-ecommerce.com"

# Replace with the actual locators for elements on the website
PRODUCT_ITEM = "//div[@class='product-item']"
ADD_TO_CART_BUTTON = "//button[contains(text(), 'Add to Cart')]"
CART_LINK = "//a[contains(text(), 'Cart')]"
CHECKOUT_BUTTON = "//button[contains(text(), 'Checkout')]"
FIRST_NAME_FIELD = "firstName"
LAST_NAME_FIELD = "lastName"
EMAIL_FIELD = "email"
ADDRESS_FIELD = "address"
CITY_FIELD = "city"
STATE_FIELD = "state"
ZIP_CODE_FIELD = "zipCode"
CARD_NUMBER_FIELD = "cardNumber"
EXPIRY_DATE_FIELD = "expiryDate"
CVV_FIELD = "cvv"
PLACE_ORDER_BUTTON = "//button[contains(text(), 'Place Order')]"
SUCCESS_MESSAGE = "Your order has been placed successfully!"

@pytest.fixture(scope="class")
def driver():
    driver = webdriver.Chrome()  # Replace with your preferred driver
    yield driver
    driver.quit()

def test_checkout_process(driver):
    driver.get(BASE_URL)

    # Add an item to the cart
    product_item = driver.find_element(By.XPATH, PRODUCT_ITEM)
    product_item.find_element(By.XPATH, ADD_TO_CART_BUTTON).click()

    # Navigate to the cart page
    driver.find_element(By.XPATH, CART_LINK).click()
    WebDriverWait(driver, 10).until(EC.presence_of_element_located((By.XPATH, CHECKOUT_BUTTON)))

    # Proceed to checkout
    driver.find_element(By.XPATH, CHECKOUT_BUTTON).click()

    # Fill out checkout form
    driver.find_element(By.ID, FIRST_NAME_FIELD).send_keys("John")
    driver.find_element(By.ID, LAST_NAME_FIELD).send_keys("Doe")
    driver.find_element(By.ID, EMAIL_FIELD).send_keys("john.doe@example.com")
    driver.find_element(By.ID, ADDRESS_FIELD).send_keys("123 Main St")
    driver.find_element(By.ID, CITY_FIELD).send_keys("Anytown")
    driver.find_element(By.ID, STATE_FIELD).send_keys("CA")
    driver.find_element(By.ID, ZIP_CODE_FIELD).send_keys("12345")
    driver.find_element(By.ID, CARD_NUMBER_FIELD).send_keys("1234567890123456")
    driver.find_element(By.ID, EXPIRY_DATE_FIELD).send_keys("12/25")
    driver.find_element(By.ID, CVV_FIELD).send_keys("123")

    # Place the order
    driver.find_element(By.XPATH, PLACE_ORDER_BUTTON).click()

    # Verify success message
    WebDriverWait(driver, 10).until(EC.text_to_be_present_in_element((By.XPATH, "//div[@class='success-message']"), SUCCESS_MESSAGE))
    assert SUCCESS_MESSAGE in driver.page_source

    # Verify page transitions (example - check for cart page after adding item)
    assert CART_LINK in driver.page_source

    # Verify form validation messages (example - empty first name field)
    driver.find_element(By.ID, FIRST_NAME_FIELD).clear()
    driver.find_element(By.XPATH, PLACE_ORDER_BUTTON).click()
    assert "Please enter your first name" in driver.page_source
