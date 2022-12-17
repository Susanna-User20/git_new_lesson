# git_new_lessonimport pytest
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

class TestMY:

    def amound_of_views(self):
        driver=webdriver.Chrome()
        search = 'Believer from Imagine Dragons'
        driver.get("https://www.youtube.com/results?search_query=" + search)
        main = WebDriverWait(driver, 10).until(
            EC.presence_of_element_located((By.ID, "metadata")))
        data = main.find_elements_by_id("metadata-line")
        for datas in data:
            views = datas.find_element_by_xpath("""//*[@id="metadata-line"]/span[1]""")
        return views.text


    def test_1(self): 
        views = self.amound_of_views()
        if not "B" in views or "M" in views:
            pytest.xfail("the amound of views is less")
