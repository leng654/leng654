from selenium import webdriver
from selenium.webdriver.common.keys import Keys
import time

# 初始化WebDriver
driver = webdriver.Chrome()

# 打开Tinder网站
driver.get("https://tinder.com")

# 等待页面加载
time.sleep(5)

# 找到并点击登录按钮
login_button = driver.find_element_by_xpath("//button[text()='Log in']")
login_button.click()

# 等待弹出窗口加载
time.sleep(5)

# 选择通过Google登录
google_login = driver.find_element_by_xpath("//span[text()='Log in with Google']")
google_login.click()

# 切换到Google登录窗口
driver.switch_to.window(driver.window_handles[1])

# 输入Google邮箱
email_field = driver.find_element_by_xpath("//input[@type='email']")
email_field.send_keys("your_email@gmail.com")
email_field.send_keys(Keys.RETURN)

# 等待并输入密码
time.sleep(3)
password_field = driver.find_element_by_xpath("//input[@type='password']")
password_field.send_keys("your_password")
password_field.send_keys(Keys.RETURN)

# 切换回主窗口
driver.switch_to.window(driver.window_handles[0])

# 等待页面加载
time.sleep(5)

# 继续其他自动化操作，如填写个人信息等
