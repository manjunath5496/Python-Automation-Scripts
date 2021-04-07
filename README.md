### **Python Automation Scripts:**

---------------------------------------


```python

from selenium import webdriver
from selenium.webdriver.common.keys import Keys

driver = webdriver.Chrome('chromedriver.exe')
driver.get("https://www.python.org")
print(driver.title)
search_bar = driver.find_element_by_name("q")
search_bar.clear()
search_bar.send_keys("getting started with python")
search_bar.send_keys(Keys.RETURN)
print(driver.current_url)
driver.close()


```
----------------------------------------

---------------------------------------


```python

import time
from selenium import webdriver

driver = webdriver.Chrome('chromedriver.exe')  
driver.get('http://www.google.com/');
time.sleep(5) 
search_box = driver.find_element_by_name('q')
search_box.send_keys('ChromeDriver')
search_box.submit()
time.sleep(5) 
driver.quit()


```
----------------------------------------

---------------------------------------


```python

import time

from selenium import webdriver
from selenium.webdriver.chrome.service import Service

service = Service('chromedriver.exe')
service.start()
driver = webdriver.Remote(service.service_url)
driver.get('http://www.google.com/');
time.sleep(5) 
driver.quit()



```
----------------------------------------

---------------------------------------


```python

import os
from selenium import webdriver


# get the path of ChromeDriverServer
dir = os.path.dirname(__file__)
chrome_driver_path = "chromedriver.exe"

# create a new Chrome session
driver = webdriver.Chrome(chrome_driver_path)
driver.implicitly_wait(30)
driver.maximize_window()

# Navigate to the application home page
driver.get("http://www.google.com")

# get the search textbox
search_field = driver.find_element_by_name("q")

# enter search keyword and submit
search_field.send_keys("Selenium WebDriver Interview questions")
search_field.submit()

# get the list of elements which are displayed after the search
# currently on result page using find_elements_by_class_name method
lists = driver.find_elements_by_class_name("r")

# get the number of elements found
print ("Found " + str(len(lists)) + " searches:")

# iterate through each element and print the text that is
# name of the search

i=0
for listitem in lists:
   print (listitem.get_attribute("innerHTML"))
   i=i+1
   if(i>10):
      break

# close the browser window
driver.quit()



```
----------------------------------------


---------------------------------------


```python

from selenium import webdriver
import time
  
# set webdriver path here it may vary
brower = webdriver.Chrome(executable_path ="chromedriver.exe")
  
website_URL ="https://www.google.co.in/"
brower.get(website_URL)
  
# After how many seconds you want to refresh the webpage
# Few website count view if you stay there
# for a particular time
# you have to figure that out
refreshrate = int(15)
  
# This would keep running until you stop the compiler.
while True:
    time.sleep(refreshrate)
    brower.refresh()




```
----------------------------------------


---------------------------------------


```python

from selenium import webdriver
# sleep() function is required because
# selenium needs a page to be fully loaded first
# otherwise errors may occur
from time import sleep
# Usage sleep(x) Where x is time in seconds and
# may vary according to your connection
  
# I have made class so that extra methods can be added later on
# if required
class instagramBot:
    def __init__(self, username, password):
        # these lines will help if someone faces issues like
        # chrome closes after execution
        self.opts = webdriver.ChromeOptions()
        self.opts.add_experimental_option("detach", True)
        self.driver  = webdriver.Chrome(options=self.opts)
          
        # Username and password
        self.username = username
        self.password = password
          
        # Opens Instagram login page
        self.driver.get("https://instagram.com")
        sleep(2) # 1 Second Wait
          
        # Automatically enters your username and 
        # password to instagram's username field
        self.driver.find_element_by_xpath("//input[@name = 'username']").send_keys(self.username)
        self.driver.find_element_by_xpath("//input[@name = 'password']").send_keys(self.password)
          
        # Clicks on Log In Button
        self.driver.find_element_by_xpath("//div[contains(text(), 'Log In')]").click()
        sleep(2)
  
        # Bonus: Automatically clicks on 'Not Now' 
        # when Instagram asks to show notifications
        self.driver.find_element_by_xpath("//button[contains(text(), 'Not Now')]").click()
  
# Testing Your Code
instagramBot('Sample Username','Sample Password')




```
----------------------------------------






