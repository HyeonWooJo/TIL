## Restful API

<br>

<img src = "https://www.notion.so/Restful-API-36d07332325849e7ba535dc5800a0800#a87cacde5d6a4f44ac2d86373bc9db92">

### 1. 정의
- REST는 Representational State Transfer의 줄임말로 **웹에 존재하는 모든 자원(이미지, 동영상, DB 자원)에 고유한 URI를 부여해 활용한다는 뜻이다**. REST는 프로토콜이나 표준이 아닌 아키텍처 원칙이다.
- RESTful API는 HTTP URI(Uniform Resource Identifier)를 통해 자원(Resource)을 명시하고, HTTP Method(POST, GET, PUT, DELETE)를 통해 해당 자원에 대한 CRUD Operation을 적용하는 API를 의미한다.

<br>

---

### 2. REST개념이 대두된 이유
- 큰 특징으로는 '애플리케이션 분리 및 통합', '다양한 클라이언트의 등장'이다.
    - 애플리케이션의 복잡도가 증가하면서 애플리케이션을 어떻게 분리하고 통합하느냐가 주요 이슈가 되었다.
    - 모바일과 같은 다양한 클라이언트의 등장하면서 Backend 하나로 다양한 Device를 대응하기 위해 REST의 필요성이 증대되었다.

<br>

---

### 3. REST의 구성
- 자원(Resource): URI
    - 모든 자원에 고유한 ID가 존재하고, 이 자원은 Server에 존재한다.
    - 자원을 구별하는 ID는 ‘/groups/:group_id’와 같은 HTTP URI 다.
    - Client는 URI를 이용해서 자원을 지정하고 해당 자원의 상태(정보)에 대한 조작을 Server에 요청한다.
- 행위(Verb): HTTP Method
    - HTTP 프로토콜의 Method를 사용한다.
    - HTTP 프로토콜은 GET, POST, PUT, DELETE 와 같은 메서드를 제공한다.
- 표현(Representation of Resource)
    - Client가 자원의 상태(정보)에 대한 조작을 요청하면, Server는 이에 적절한 응답(Representation)을 보낸다.
    - REST에서 하나의 자원은 JSON, XML, TEXT, RSS 등 여러 형태의 Representation으로 나타내어 질 수 있다.
    - JSON 혹은 XML를 통해 데이터를 주고 받는 것이 일반적이다.


<br>

---

### 4. REST의 특징
1. **Uniform (유니폼 인터페이스)**
- HTTP 표준에만 따른다면, 안드로이드/IOS 플랫폼이든, 특정 언어나 기술에 종속되지 않고 모든 플랫폼에 사용이 가능하며, URI로 지정한 리소스에 대한 조작이 가능한 아키텍처 스타일을 의미한다.
2. **Stateless (무상태성)** 
- HTTP는 Stateless Protocol 이므로, REST 역시 무상태성을 갖는다. 즉, HttpSession과 같은 컨텍스트 저장소에 상태정보를 따로 저장하고 관리하지 않고, API 서버는 들어오는 요청만을 단순 처리하면 된다. 세션과 같은 컨텍스트 정보를 신경쓸 필요가 없어 구현이 단순해진다.
3. **Cacheable (캐시가능)**
- HTTP 기존의 웹 표준을 그대로 사용하므로, 웹에서 사용하는 기존의 인프라를 그대로 활용 가능하다. HTTP 프로토콜 기반의 로드밸런서(mod_proxy)나, SSL은 물론이고 HTTP가 가진 가장 강력한 특징 중의 하나인 캐싱 기능을 적용할 수 있다. 일반적인 서비스에서 조회 기능이 주로 사용됨을 감안하면, HTTP 리소스들을 웹 캐쉬 서버 등에 캐싱하는 것은 용량이나 성능 면에서 이점이 있다. 캐싱 구현은 HTTP 프로토콜 표준에서 사용하는 Last-Modified 태그나 E-Tag를 이용하면 가능하다. 대량의 요청을 효율적으로 처리하기 위해 캐시가 요구된다. 캐시 사용을 통해 응답시간이 빨라지고 REST Server 트랜잭션이 발생하지 않기 때문에 전체 응답시간, 성능, 서버의 자원 이용률을 향상시킬 수 있다.
4. **Self-descriptiveness (자체 표현 구조)**
- 동사(Method) + 명사(URI) 로 이루어져있어 어떤 메서드에 무슨 행위를 하는지 알 수 있으며, 메시지 포맷 역시 JSON을 이용해서 직관적으로 이해가 가능한 구조로, REST API 메시지만 보고도 이를 쉽게 이해할 수 있다.
5.  **Client - Server 구조**
- REST 서버는 API 제공, 클라이언트는 사용자 인증이나 컨텍스트(세션, 로그인 정보 등)을 직접 관리하는 구조로 각각의 역할이 확실히 구분되기 때문에, 클라이언트와 서버에서 개발해야 할 내용이 명확해지고 서로간 의존성이 줄어들게 된다.
6. **계층형 구조** 
- API 서버는 순수 비지니스 로직을 수행하고, 그 앞단에 사용자 인증, 암호화(ssl), 로드밸런싱 등을 하는 계층을 추가하여 구조상의 유연상을 둘 수 있다.


<br>

---

### 5. REST의 설계
- URI는 정보의 자원을 표현해야 한다.(리소스명은 동사보다는 명사를 사용)
- 자원에 대한 행위는 HTTP Method(GET, POST, PUT, DELETE 등)으로 표현해야 한다.

<br>
---

### 6. URI 설계시 주의할 점
- 슬래시 구분자(/)는 계층 관계를 나타내는데 사용
- URI 마지막 문자로 슬래시(/)를 포함하지 않는다.
- 하이픈(-)은 URI 가독성을 높이는데 사용
- 밑줄(_)은 URI에 사용하지 않는다.
- URI 경로에는 소문자가 적합하다.
- 파일확장자는 URI에 포함하지 않는다.


