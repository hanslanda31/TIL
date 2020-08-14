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

2. login 
<img width="1792" alt="3" src="https://user-images.githubusercontent.com/60166685/90249914-3ed6e780-de76-11ea-8808-6b951bcf2c5a.png">

```pyhthon
# 로그인 페이지 이동
driver.find_element_by_xpath('//*[@id="gnb_login_button"]/span[3]').click()

# 아이디, 패스워드
user = "user"
pw = "password"
driver.find_element_by_xpath('//*[@id="id"]').send_keys(user)
driver.find_element_by_xpath('//*[@id="pw"]').send_keys(pw)

# 로그인 버튼 클릭
driver.find_element_by_xpath('//*[@id="log.login"]').click()

# 카풀 게시판 클릭
driver.find_element_by_xpath('//*[@id="menuLink2"]').click()
```

3.  target page move 
<img width="1792" alt="4" src="https://user-images.githubusercontent.com/60166685/90249919-40081480-de76-11ea-9097-4513a650c756.png">

```python
# 카풀 게시판 클릭
driver.find_element_by_xpath('//*[@id="menuLink2"]').click()
```

4. 15page -> 50page 
  - 카풀 게시판 초기화면은 게시물이 15개만 나온다
  - 50개씩 나오도록 변경 

<img width="1792" alt="5-1" src="https://user-images.githubusercontent.com/60166685/90249926-41d1d800-de76-11ea-9128-d7be97b209b1.png">
<img width="1792" alt="5-2" src="https://user-images.githubusercontent.com/60166685/90249935-43030500-de76-11ea-9131-f72edc373860.png">
<img width="1792" alt="5-3" src="https://user-images.githubusercontent.com/60166685/90250896-cf61f780-de77-11ea-8a52-76e89417f0d8.png">

```python
# 50개 페이지 가져오는 url 

url = "https://cafe.naver.com/surfxiframe_url=/ArticleList.nhn%\
3Fsearch.clubid=22509719%26search.boardtype=L%26search.menuid=2%26search.marketBoardTab=\
D%26search.specialmenutype=%26userDisplay=50"

```
  





