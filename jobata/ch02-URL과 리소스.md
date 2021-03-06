# 2장 URL과 리소스

## CONTENTS
- [인터넷의 리소스 탐색하기](#인터넷의-리소스-탐색하기)
- [URL 문법](#URL-문법)
- [단축 URL](#단축-URL)
- [안전하지 않은 문자](#안전하지-않은-문자)
- [스킴의 바다](#스킴의-바다)
- [미래](#미래)

### 인터넷의 리소스 탐색하기
- url
  - uniform resource locator, 통합 자원 지시자
  - 애플리케이션이 리소스에 접근할 수 있는 방법을 제공한다.
    - url은 당신과 브라우저에게 정보 찾는데 필요한 모든 것을 제공하며 원하는 리소스가 어디에 위치하고 어떻게 가져오는지 정의한다.
- url의 구조
  - `스킴://서버위치/경로`
  - 인터넷상의 모든 리소스를 가리키고 가져오기 위해 모든 사람이 같은 방식으로 이름을 써서 리소스를 가져올 수 있도록 단일 방식의 작명 규칙을 가진 것
- http://www.joes-hardware.com/seasonal/index-fall.html이라는 url
  - url의 첫 부분인 http는 url의 스킴이다.
    - 스킴은 웹 클라이언트가 리소스에 어떻게 접근하는지 알려준다.
    - 이 경우에는 url이 http 프로토콜을 사용한다.
  - 2번째 부분인 www.joes-hardware.com은 서버의 위치다.
    - 웹 클라이언트가 리소스가 어디에 호스팅 되어 있는지 알려준다.
  - 3번재 부분인 /seasonal/index-fall.html은 리소스의 경로다.
    - 서버에 존재하는 로컬 리소스들 중에서 요청받은 리소스가 무엇인지 알려준다.

### URL 문법
- URL 스킵의 문법은 일반적으로 9개 부분으로 나뉜다.
  - `<스킴>://<사용자 이름>:<비밀번호>@<호스트>:<포트>/<경로>;<파라미터>?<질의>#<프래그먼트>`
    - 이 모든 컴포넌트를 가지는 url은 거의 없다. 가장 중요한 컴포넌트는 스킴, 호스트, 경로다.

컴포넌트|설명|기본값
---|---|---
스킴|리소스를 가져오려면 어떤 프로토콜을 사용하여 서버에 접근해야 하는지 가리킨다.|없음
사용자 이름|몇몇 스킴은 리소스에 접근을 하기 위해 사용자 이름을 필요로 한다.|anonumous
비밀번호|사용자의 비밀번호 가리키며, 사용자 이름에 콜론(:)으로 이어서 기술한다.|<이메일 주소>
호스트|리소스를 호스팅하는 서버의 호스트 명이나 IP 주소|없음
포트|리소스를 호스팅하는 서버가 열어놓은 포트번호. 많은 스킴이 기본 포트를 가지고 있다.(http의 기본 포트는 80이다)|스킴에 따라 다름
경로|이전 컴포넌트와 빗금(/)으로 구분되어 있으며, 서버 내 리소스가 서버 어디에 있는지를 가리킨다. 경로 컴포넌트의 문법은 서버와 스킴에 따라 다르다. (url의 경로를 세그먼트로 나눌 수 있고, 각 세그먼트는 자체 컴포넌트를 가질 수 있다.)|없음
파라미터|특정 스킴들에서 입력 파라미터를 기술하는 용도로 사용한다. 파라미터는 이름/값을 쌍으로 가진다. 파라미터는, 다른 파라미터나 경로의 일부와 세미콜론(;)으로 구분하여 기술하며, 여러 개를 가질 수 있다.|없음
질의|스킴에서 애플리케이션(데이터베이스, 게시판, 검색엔진, 기타 인터넷 게이트웨이)에 파라미터를 전달하는데 쓰인다. 질의 컴포넌트를 작성하는데 쓰이는 공통 포맷은 없다. 이는 url의 끝에 "?"로 구분한다.|없음
프래그먼트|리소스의 조각이나 일부분을 가리키는 이름이다. url이 특정 객체를 기리킬 경우에 프래그먼트 필드는 서버에 전달되지 않는다. 이는 클라이언트에서만 사용한다. url의 끝에서 "#"문자로 구분한다.|없음

- 스킴: 사용할 프로토콜
  - 주어진 리소스에 어떻게 접근한는지 알려주는 중요한 정보다.
  - url을 해석하는 애플리케이션이 어떤 프로토콜을 사용하여 리소스를 요청해야 하는지 알려준다.
  - 알파벳으로 시작한다. 대소문자를 가리지 않는다.
  - url의 나머지 부분들과 첫 번째 ':' 문자로 구분한다.
- 호스트와 포트
  - 애플리케이션이 인터넷에 있는 리소스를 찾으려면 리소스를 호스팅하고 있는 장비와 그 장비 내에서 리소스에 접근할 수 있는 서버가 어디에 있는지 알아야 한다.
  - 호스트와 포트 컴포넌트는 그 두가지 정보를 제공해 준다.
    - 호스트 컴포넌트는 접근하려고 하는 리소스를 가지고 있는 인터넷상의 호스트 장비를 가리킨다.
    - 포트 컴포넌트는 서버가 열어놓은 네트워크 포트를 가리킨다.
- 사용자 이름과 비밀번호
  - 많은 서버가 자신이 가지고 있는 데이터에 접근을 허용하기 전에 사용자 이름과 비밀번호를 요구한다.
  - ftp://ftp.prep.ai.mit.edu/pub/gnu
    - 사용자 이름이나 비밀번호 컴포넌트가 없이 표준 스킴, 호스트, 경로만 있다.
    - 그 값들이 삽입되어 있지 않을 경우 기본 사용자 이름과 비밀번호 값을 넣어놓을 것이다.
      - 기본 사용자 이름 : anonymous
      - 기본 비밀번호 : IE는 IEUser, 크롬은 chrome@example.com
  - ftp://anonymous@gtp.prep.ai.miut.edu/pub/gnu
    - 사용자 이름이 anonymous로 되어 있다.
    - 호스트 컴포넌트와 나란히 기술되어 있는 사용자 이름은 단순한 이메일 주소처럼 보이기도 한다.
    - '@' 문자는 url로부터 사용자 이름과 비밀번호 컴포넌트를 분리한다.
  - ftp://anonymous:my_passwd@ftp.prep.ai.mit.edu/pub/gnu
    - 사용자 이름 anoymous와 비밀번호 my_passwd를 ':' 문자로 분리하여 모두 기술하였다.
- 경로
  - 리소스가 서버의 어디에 있는지 알려준다.
  - 계층적 파일 시스템 경로와 유사한 구조를 가진다.
  - '/' 문자를 기준으로 경로조각으로 나뉜다.
    - 각 경로조각은 자체만의 파라미터 컴포넌트를 가질 수 있다.
- 파라미터
  - 많은 스킴이 객체에 대한 호스트 및 경로 정보만으로는 리소스를 찾지 못한다.
  - 이름/값 쌍의 리스트로 url 나머지 부분들로부터 ';' 문자로 구분하여 url에 기술한다.
  - http://www.joes-hardware.com/hammers;sale=false/index.html;graphics=true
    - hammers와 index.html이라는 두 개의 경로조각이 있다.
      - hammers의 경로조각은 값이 false인 sale이라는 파라미터를 가진다.
      - index.html 경로조각은 값이 true인 graphicss란 파라미터를 가진다.
- 질의 문자열
  - 데이터베이스 같은 서비스들은 요청받을 리소스 형식의 범위는 좁히기 위해서 질문이나 질의를 받을 수 있다.
  - '?'의 우측에 있는 값이다.
  - 게이트웨이를 가리키는 url의 경로 컴포넌트와 함게 전달한다.
    - 게이트웨이 : 다른 애플리케이션에 접근하려고 할 때 거치는 통로
  - http://www.joes-hardware.com/inventory-check.cgi?item=12731&color=blue&size=large
    - 죠의 컴퓨터 가게에 재고 확인을 하기 위해 게이트웨이 서버로 전달하는 질의 컴포넌트의 예
    - 질의는 제품번호가 12731이고 파란색에 큰 치수인 물품의 재고가 있는지 검사한다.
    - 많은 게이트웨이가 '&'로 나뉜 '이름=값' 쌍 형식의 질의 문자열을 원한다.
- 프래그먼트
  - 리소스의 특정 부분을 가리킬 수 있도록 url은 리소스 내의 조각을 가리킬 수 있는 프래그먼트 컴포넌트를 제공한다.
    - html 같은 리소스 형식들은 본래의 수준보다 더 작게 나뉠 수 있다.
      - html 문서에 있는 특정 이미지나 일부분을 가리킬 수 있다.
  - 일반적으로 http 서버는 객체 일부가 아닌 전체를 다루기 때문에 클라이언트는 서버에 프래그먼트를 전달하지 않는다.
    - 브라우저가 서버로부터 전체 리소스를 내려받은 후, 프래그먼트를 사용하여 당신이 보고자 하는 리소스의 일부를 보여준다.
  - http://www.joes-hardware.com/tools.html#drills
    - 사용자가 http://www.joes-hardware.com/tools.html#drills를 가리키는 링크를 선택한다.
    - 브라우전는 http://www.joes-hardware.com/tools.html를 요청한다.
    - 서버는 전체 html 페이지를 반환한다.
    - 브라우저는 'drills' 프래그먼트로 시작하는 html 페이지를 보여준다.
      - 브라우저는 'drills' 프래그먼트에 시작부로 스크롤을 내린다.

### 단축 URL
- 웹 클라이언트는 몇몇 단축 url을 인식하고 사용한다.
  - 상대 url은 리소스 안에 있는 리소스를 간결하게 기술하는데 사용할 수 있다.
  - 많은 브라우저가 사용자가 기억하고 있는 url 일부를 입력하면 나머지 부분을 자동으로 입력해주는 url 자동 확장을 지원한다.
- 상대 url
  - url을 짧게 표기하는 방식
  - 상대 url로 리소스에 접근하는데 필요한 모든 정보를 얻기 위해서는, 기저(base)라고 하는 다른 url을 사용해야 한다.
  - 프래그먼트이거나 url의 일부
- url을 처리하는 브라우저 같은 애플리케이션은 상대 url과 절대 url 간에 상호 변환을 할 수 있어야 한다.
- 상대 url을 절대 url로 변환하기
  - 변환 과정의 첫 단계는 기저 url을 찾는 것. 기저 url은 상대 url의 기준이 된다.
    - 리소스에서 명시적으로 제공
      - html 문서에서 기저 url을 가리키는 `<BASE>` html 태그
    - 리소스를 포함하고 있는 기저 url
      - 기저 url이 명시되지 않은 리소스에 포함된 경우 해당 리소스의 url을 기저 url로 쓸 수 있다.
    - 기저 url이 없을 경우
      - 보툥 이런 경우 절대 url만으로 이루어져 있다. but, 불완전하거나 깨진 url일 수도 있음.
  - 다음 단계는 상대 url과 기저 url을 각각의 컴포넌트 조각으로 나누는 것
    - url 파싱, url 분해하기
  - 파싱된 상태 url을 RFC 1808에 최초로 기술된 알고리즘을 사용하여 절대 경로 형태로 변환한다.
- url 확장
  - 호스트명 확장
    - 단순한 휴리스틱만을 사용해서 입력한 호스트 명을 전체 호스트 명으로 확장할 수 있다.
    - 예) yahoo를 입력하면 자동으로 호스트 명에 www. 와 .com 을 붙여서 만들어줌
    - 호스트 명에 대한 확장 기능은 프락시와 같은 다른 http 애플리케이션에 문제를 발생시킬 수도 있다.
  - 히스토리 확장
    - 과거에 사용자가 방문했던 url의 기록을 저장해 놓는 것이다.
    - 입력된 url의 앞 글자들을 포함하는 완결된 형태의 url들을 선택하게 해준다.

### 안전하지 않은 문자
- url
  - 안전한 전송
    - 모든 프로토콜이 데이터를 전송하기 위해서 서로 다른 장치를 가지고 있기 때문에, 어떤 인터넷 프로토콜을 통해서든 안전하게 전송될 수 있도록 url을 설계하는 것이 중요
    - 정보가 유실될 위험 없이 url을 전송할 수 있다는 것
    - 상대적으로 작고 일반적으로 안전한 알파벳 문자만 포함하도록
  - 좋은 가독성
    - 출력이 되지 않거나 보이지 않은 문자, 변환될 수 있다 하더라도 그런 문자들을 사용하는 것은 금지
  - 알파벳 이외의 문자
    - 이스케이프 기능 추가, 안전하지 않은 문자를 안전한 문자로 인코딩
- url에서 사용할 수 있는 알파벳과 인코딩 규칙
  - url 문자 집합
    - 이스케이프 문자열
      - US_ASCII에서 사용이 금지된 문자들, 특정 문자나 데이터를 인코딩할 수 있게함
  - 인코딩 체계
    - 안전하지 않은 문자를 이스케이프 문자로 바꾼다.
      - '%'로 시작해 ASCII 코드로 표현되는 두 개의 16진수 숫자로 이루어짐
  - 문자 제한
    - `%` : 인코딩 이스케이프 토큰
    - `/` : 경로 컴포넌트 세그먼트를 나누는 용도
    - `.` : 경로 컴포넌트에서 사용
    - `..` : 경로 컴포넌트에서 사용
    - `#` : fragment 컴포넌트에서 사용
    - `?` : 쿼리파라미터 컴포넌트에서 사용
    - `;` : 매트릭스 파라미터 컴포넌트에서 사용
    - `:` : 스킴, 사용자 이름/비밀번호, 호스트/포트의 구획문자로 사용
    - `$` : 선점
    - `+` : 선점
    - `{` `}` `|` `\` `~` `[` `]` : 게이트웨이와 같은 여러 전송 에이전트에서 불안하게 다루기 때문에 제한됨
    - `<` `>` `"` : 안전하지 않음. 웹 문서에서 URL을 구분지어 표시s하듯이 URL 범위 밖에서 역할이 있는 문자이기 때문에 반드시 인코딩해야한다.
    - `0x00-0x1F` `0x7F` : 제한됨. 이 16진수 범위에 속하는 문자들은 인쇄되지 않는 US-ASCII 문자다.
    - `>` `0x7F` : 제한됨. 이 16진수 범위에 속하는 문자들은 7비트 US-ASCII 문자가 아니다.

### 스킴의 바다
- http
  - `http://<호스트>:<포트>/<경로>?<질의>#<프래그먼트>`
    - `http://www.joes-hardware.com/index.html`
  - 사용자 이름이나 비밀번호가 없다는 것을 제외하고는 일반 url 포맷을 지키는 하이퍼 텍스트 전송 프로토콜 스킴. 포트값이 생략되어 있으면 기본 값은 80이다.
- https
  - `https://<호스트>:<포트>/<경로>?<질의>#<프래그먼트>`
    - `https://www.joes-hardware.com/secure.html`
  - http 스킴과 거의 같다. 다른 점이라고는 http 커넥션의 양 끝단에서 암호화하기 위해 넷스케이프에서 개발한 SSL(Secure Sockets Layer)을 사용한다. 기본 포트값은 443이다.
- ftp
  - `ftp://<사용자 이름>:<비밀번호>@<호스트>:<포트>/<경로>;<파라미터>`
    - `ftp://anonymous:joe%40joes-hardware.com@prep.ai.mit.edu:21/pub/gnu/`
  - 파일 전송 프로토콜은 ftp 서버에 있는 파일을 내려 받거나 올리고 ftp 서버의 디렉터리에 있는 콘텐츠 목록을 가져오는데 사용할 수 있다.
  - 웹과 url이 출현하기 전부터 있었다.
  - 웹 애플리케이션은 데이터에 접근하는 용도의 스킴으로 ftp를 사용한다.
- file
  - `file://<호스트>/<경로>`
    - `file://OFFICE-FS/policies/casual-fridays.doc`
  - file 스킴은 주어진 호스트 기기(로컬 디스크, 네트워크 파일 시스템, 기타 파일 공유 시스템)에서 바로 접근할 수 있는 파일들
  - 만약 호스트가 생략되어 있으면 url을 사용하고 있는 기기의 로컬 호스트가 기본값이 된다.
- telnet
  - `telnet://<사용자 이름>:<비밀번호>@<호스트>:<포트>/`
    - `telnet://slurp:webhound@joes-hardware.com:23/`
  - telnet 스킴은 대화형 서비스에 접근하는데 사용한다.
  - telnet url 자체가 객체를 가리키지는 않지만, 리소스라고 할 수 있는 대화형 애플리케이션은 이 telnet 프로토콜을 통해 접근할 수 있다.
- mailto
  - `mailto:<RFC-822-addr-spec>`
    - `mailto:joe@joes-hardware.com`
  - 이메일 주소를 가리킨다.
  - 이메일은 다른 스킴과는 다르게 동작하기 때문에 표준 url과는 다른 포멧을 가진다.
  - 인터넷 이메일 주소의 문법은 RFC 822에 기술되어 있다.
- rtsp, rtspu
  - `<rtsp or rtspu>://<사용자 이름>:<비밀번호>@<호스트>:<포트>/<경로>`
    - `rtsp://www.joes-harware.com:554/interview/cto_video`
  - 실시간 스트리밍 프로토콜(Real Time Streaming Protocol)을 통해서 읽을 수 있는 오디오 및 비디오와 같은 미디어 리소스 식별자다
  - rtspu 스킴에 있는 u는 리소스를 읽기 위해서 udp 프로토콜이 사용됨을 뜻한다.
- news
  - `news:<newsgroup or news-article-id>`
    - `news:rec.arts.startrek`
  - 특정 문서나 뉴스 그룹에 접근하는데 사용한다.
  - 리소스의 위치 정보를 충분히 포함하지 않는 특이한 속성이 있다.
  - 사용자로부터 그 정보를 알아내는 것은 애플리케이션ㄴ의 몫이다.
  - url을 입력받은 브라우저는 현재 설명되어 있는 뉴스 서버 정보를 사용하여 어떤 서버로부터 뉴스를 가져올지 결정한다.
  - 뉴스 리소스는 위치에 독립적이다.
    - 하나의 서버로만 접근할 수 있는게 아니라 여러 서버를 통해 접근할 수 있다.
  - news url에서 선점한 @ 문자는 뉴스 그룹을 가리키는 뉴스 url과 특정 뉴스 문서를 가리키는 뉴스 url을 구분ㄴ하기 위해 사용된다.

### 미래
- url은 강력한 도구다.
  - 세상에 존재하는 모든 객체에 이름을 지을 수 있다.
  - 새로운 포맷을 쉽게 추가할 수 있다.
  - 인터넷 프로토콜 간에 공유할 수 있는 일관된 작명 규칙을 제공한다.
- url이 완벽한 것은 아니다.
  - 주소이지 실제 이름은 아니다.
    - 특정 시점에 어떤 것이 위치한 곳을 알려준다는 것을 뜻한다.
    - 리소스를 찾는데 필요한 포트와 서버 이름을 제공한다.
    - 리소스가 옮겨지면 더는 사용할 수 없다. 그 시점에 기존 url이 가리키고 있던 객체를 찾을 방법이 없어진다.
  - 예방 방법?
    - URN
