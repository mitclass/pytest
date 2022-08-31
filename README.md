# pytest
Pytest is a testing framework based on Python Programming. It is the most powerful Test-Driven Framework among all Testing Frameworks available in the Software Development Industry! It's very similar to JUnit & TestNG framework in Java Stack but more features and more powerful.

Pytest will only consider the following as test cases:
a) File names starts with test_*.py or *_test.py: test_login.py/login_test.py
b) Functions starts with test_*() or, *_test() ill be considered as test cases
c) Classes starts with test_* or *_test

# Installation Process:
1. pip install pytest

# Pytest Framework Demo:

import pytest

from selenium import webdriver

from selenium.webdriver.common.by import By

from webdriver_manager.chrome import ChromeDriverManager

def getData():

    return [
        ("abcd@gmail.com", "abcd123"),
        ("abcde@gmail.com", "abcd1234"),
        ("abcdef@gmail.com", "abcd12345")
    ]

def setup_function():
    global driver
    driver = webdriver.Chrome(executable_path = ChromeDriverManager().install())
    driver.get("http://facebook.com/")
    driver.maximize_window()

def teardown_function():
    driver.close()
    driver.quit()

@pytest.mark.parametrize("username, password", getData())
def test_login(username, password):
    driver.find_element(By.ID, "email").send_keys(username)
    driver.find_element(By.ID, "pass").send_keys(username)
    driver.find_element(By.id, "submit").click()
