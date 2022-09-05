## Body data 호출 방법

Django에서 POST request의 body 안에 있는 데이터를 가져오는 방법은 여러 가지이다.
보통 data = json.loads(request.body)로 data를 선언하여 안에서 데이터를 가져온다.

<br>

1. data["key"]
- 위와 같이 key에 대한 value값을 가져올 수 있다.
- body에 key가 없거나 key의 스펠링이 다를 경우 KEY ERROR가 발생한다.
- KEY ERROR를 확실하게 발생하고 싶을 경우 사용한다.

<br>

---

2. data.get("key")
- 1번과 다르게 body에 key가 없거난 스펠링 다를 경우 KEY ERROR가 발생하지 않는다.
- 대신 위처럼 "key"외에 다른 인자를 주지 않을 경우 기본값으로 None을 반환한다.
- data.get("key", 1)처럼 1을 인자를 줄 경우 None이 아닌 1을 반환한다.
- KEY ERROR를 발생하지 않게 하고 싶을 경우 사용한다.
