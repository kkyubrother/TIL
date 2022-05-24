# Colab에서 Selenium 구동
## 문제
1. 크롬 드라이버
2. 화면이 없음

## 크롬 드라이버
> 크롬 드라이버를 apt를 이용해 설치
```shell
# install browser and driver
apt install chromium-browser chromium-driver

# install selenium
pip install selenium
```
> 크롬 구동시 화면 출력을 하지 않음
```python
from selenium import webdriver


# 크롬 옵션 설정
options = webdriver.ChromeOptions()
# 화면 출력 생략
options.add_argument("--headless")
# 샌드박스 비활성화
# colab은 해당 기능을 지원하지 않는 것으로 판단됨
options.add_argument("--no-sandbox")
# https://github.com/puppeteer/puppeteer/issues/1834#issuecomment-1094307800
# 인터넷에 해당 옵션이 많이 보이는데, 적용 안해도 실행 가능했음
# 해당 옵션을 적용하지 않았을 때 더 빠름
# options.add_argument('--disable-dev-shm-usage')

driver_path = "/usr/lib/chromium-browser/chromedriver"
driver = webdriver.Chrome(driver_path, options=options)
```