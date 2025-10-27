# 第5回 Webエンジニアリング演習 レポート
## 学籍番号（名前は書かなくてよい）
4723112
## 各エンドポイントのSwagger UIでのテスト結果
### "GET / HTTP/1.1" 200 OK
Request:
'''
curl -X 'GET' \
  'http://localhost:8000/' \
  -H 'accept: application/json'
'''
Response:
body
'''
{
  "Hello": "World"
}
'''
headers
'''
content-length: 17 
 content-type: application/json 
 date: Mon,27 Oct 2025 05:31:03 GMT 
 server: uvicorn 
'''
### "GET /health HTTP/1.1" 200 OK
Request:
'''
curl -X 'GET' \
  'http://localhost:8000/health' \
  -H 'accept: application/json'
'''
Response:
body
'''
{
  "status": "healthy"
}
'''
headers
'''
content-length: 20 
 content-type: application/json 
 date: Mon,27 Oct 2025 05:37:44 GMT 
 server: uvicorn 
'''
### "GET /items/1 HTTP/1.1" 200 OK
Request:
'''
curl -X 'GET' \
  'http://localhost:8000/items/1' \
  -H 'accept: application/json'
'''
Response:
body
'''
{
  "item_id": 1,
  "q": null
}
'''
headers
'''
content-length: 22 
 content-type: application/json 
 date: Mon,27 Oct 2025 05:39:56 GMT 
 server: uvicorn 
'''
### "GET /items/100?q=test HTTP/1.1" 200 OK
Request:
'''
curl -X 'GET' \
  'http://localhost:8000/items/100?q=test' \
  -H 'accept: application/json'
'''
Response:
body
'''
{
  "item_id": 100,
  "q": "test"
}
'''
headers
'''
 content-length: 26 
 content-type: application/json 
 date: Mon,27 Oct 2025 05:41:51 GMT 
 server: uvicorn 
'''
### "GET /items/-100 HTTP/1.1" 400 Bad Request
Request:
'''
curl -X 'GET' \
  'http://localhost:8000/items/-100' \
  -H 'accept: application/json'
'''
Response:
body
'''
{
  "detail": "Item ID must be positive"
}
'''
headers
'''
  content-length: 37 
 content-type: application/json 
 date: Mon,27 Oct 2025 05:44:39 GMT 
 server: uvicorn 
'''