# iframe 환경 크롤링 이슈

## what about 
  - selenium을 이용해 네이버 카페 크롤링 중 데이터가 불러와지지 않음(데이터가 빈값으로 들어옴)
  - 원인을 알아보니 iframe 환경으로 만들어져 있어 몇 가지 추가 작업이 필요했음 
  
## how to trouble shooting 

1. url 
<img width="1792" alt="2" src="https://user-images.githubusercontent.com/60166685/90249892-38487000-de76-11ea-8e83-620cf2efa7ab.png">

```python
url = 'https://cafe.naver.com/surfx'
driver = webdriver.Chrome()
driver.implicitly_wait(3)
driver.get(url)
```

2. 
