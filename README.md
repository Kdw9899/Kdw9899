!pip install selenium
!apt-get update
!apt install chromium-chromedriver
!pip install pyautogui

from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import pyautogui
import time
# open the homepage and maximize window
driver = webdriver.Chrome('C:\a\chromedriver.exe')
url = 'https://www.rockgarden.kr:8444/'
driver.get(url)
driver.maximize_window()

# click reservation button on the main page
reserve_btn = WebDriverWait(driver, 10).until(EC.visibility_of_element_located((By.CLASS_NAME, "icon_01"))).click()

# hit the enter to the next page
time.sleep(1)
pyautogui.hotkey('enter')
time.sleep(1)

# insert login id and password
id_insert = WebDriverWait(driver, 5).until(EC.presence_of_element_located((By.XPATH, "//*[@id='userid']"))).send_keys('insert your id')
pw_insert = WebDriverWait(driver, 5).until(EC.presence_of_element_located((By.XPATH, "//*[@id='userpw']"))).send_keys('insert your pw')
pyautogui.hotkey('enter')
time.sleep(1)
pyautogui.hotkey('enter')
pyautogui.hotkey('enter')
time.sleep(1)


# click the latest date and  pre-defined time(this case is for saturday booking and aimed to select around 09:00)
flag_btn = WebDriverWait(driver, 10).until(EC.presence_of_element_located
           ((By.XPATH, "//*[@id='wrap']/div[2]/div[3]/div[2]/ul[1]/li[2]/table[2]/tbody/tr[3]/td[7]/table/tbody/tr[2]/td/a/img"))).click()

# Please change XPATH for your time
nine_hole_0900_btn = WebDriverWait(driver, 30).until(EC.presence_of_element_located
                                                     ((By.XPATH, "//*[@id='dvTime']/li[2]/div/table/tbody/tr[21]/td[2]/a"))).click()

time.sleep(0.5)
pyautogui.hotkey('enter')

# Please change XPATH for your time
nine_hole_0900_btn = WebDriverWait(driver, 30).until(EC.presence_of_element_located
                                                     ((By.XPATH, "//*[@id='dvTime']/li[2]/div/table/tbody/tr[22]/td[2]/a"))).click()

time.sleep(0.5)
pyautogui.hotkey('enter')

# Please change XPATH for your time
nine_hole_0900_btn = WebDriverWait(driver, 30).until(EC.presence_of_element_located
                                                     ((By.XPATH, '//*[@id="dvTime"]/li[2]/div/table/tbody/tr[23]/td[2]/a'))).click()

time.sleep(0.5)
pyautogui.hotkey('enter')

# click how many ppl 

# click reservation btn

print("complete booking~ enjoy your golf~")
