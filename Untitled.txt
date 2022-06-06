




def start_driver(exclude_ip=None):
    # seleniun_ip = get_random_selenium_ip(exclude_ip)
    seleniun_ip = "172.31.17.184"
    print(seleniun_ip)
    from selenium.webdriver.common.desired_capabilities import DesiredCapabilities
    from selenium.webdriver.chrome.options import Options
    proxy = "http://JIITAKPROXYSERVICE:JIITAKPROXYSERVICE0603@jp.proxymesh.com:31280"
    capabilities = dict(DesiredCapabilities.CHROME)
    capabilities['proxy'] = {'proxyType': 'MANUAL', 'httpProxy': proxy, 'ftpProxy': proxy,
                             'sslProxy': proxy, 'noProxy': '', 'class': "org.openqa.selenium.Proxy",
                             'autodetect': False}
    chrome_options = Options()
    print("Driver started ...")
    driver = webdriver.Remote("http://" + seleniun_ip + ":4444/wd/hub", options=chrome_options)
    print("Driver initated ...")
    return driver



def get_response(url, driver):
    driver.get(url)
    # time.sleep(5)
    driver.implicitly_wait(5)
    return driver.page_source



def get_lxml_element(response):
    return html.fromstring(response)



def close_driver(driver):
    driver.quit()



def check_rankuten_stock(lxml_element):
    try:
        print("something")
        status=get_text(get_first_element(lxml_element.xpath("//table/tbody/tr/td[1]/h2/font")))
        if status:
            return False
        return True
    except:
        return True




def check_stock_status(url="https://item.rakuten.co.jp/dskatou/17697-/EMS-46747-27459662-25b7-4a57-afe2-0b27c76a7353", platform="Rakuten", search_url=None, product_name=None):
    driver = start_driver()
    response = get_response(url, driver)


    lxml_element = get_lxml_element(response)
    close_driver(driver)
    return check_rankuten_stock(lxml_element) if lxml_element is not None else None
