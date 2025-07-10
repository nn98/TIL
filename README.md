# TIL
* * *
<h3>
<details>
<summary>2025 - 01 ~ 07</summary>
<table>
  <thead>
    <tr>
      <th>순번</th>
      <th>날짜</th>
      <th>구분</th>
      <th>내용</th>
      <th>코드/참고</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align: center">1</td>
      <td style="text-align: center">2025-04-08</td>
      <td style="text-align: center"><code>JS</code></td>
      <td>
        <code>패키지 설치 및 관리</code><br>
        누더기 코딩의 대가<br>
        - 글로벌 패키지 남발<br>
        - 리액트 네이티브 초기화시 오류<br>
        <i>TypeError: cli.init is not a function</i><br>
        네이티브 구버전(안씀) 잔존<br>
        - dependency 관련 오류<br>
        - 네이티브 관련 패키지 재설치<br>
        - node npm nvm 업데이트<br>
        <br>
        하루죙일해서 딲 프로젝트 빌드까지
      </td>
      <td>
        <details><summary>Perplexity</summary>
          <code>npx react-native start --reset-cache</code><br>
          <code>npm uninstall -g react-native-cli</code><br>
          <code>npm uninstall -g react-native</code><br>
          <code>npm uninstall -g @react-native-community/cli</code><br>
          <code>npm cache clean --force</code><br>
          <code>npm install --force react-native-cli react-native</code><br>
          <code>npm install --save-dev @react-native-community/cli</code><br>
          <code>npm install --save-dev @react-native-community/cli-platform-android</code><br>
          <code>npm install --save-dev @react-native-community/cli-platform-ios</code><br>
          <code>npx react-native start --reset-cache</code><br>
          <code>npx rnx-align-deps --requirements react-native@0.76 --write</code>
        </details>
      </td>
    </tr>
    <tr>
      <td style="text-align: center">2</td>
      <td style="text-align: center">2025-04-11</td>
      <td style="text-align: center"><code>Alg</code></td>
      <td>
        <code>그래프</code><br>
        BFS-큐에 depth 1 넣고 빌때까지<br>
        DFS-스택[Stack Segment]이나 재귀<br>
        객체 사용용도에 따른 hashCode/equals 재정의
      </td>
      <td></td>
    </tr>
    <tr>
      <td style="text-align: center">3</td>
      <td style="text-align: center">2025-04-16</td>
      <td style="text-align: center"><code>JS</code><br><code>Refactoring</code></td>
      <td>
        <code>환경 변수 분리</code><br>
        환경 설정 값/환경 변수/시크릿 분리 - .env<br>
        <code>Nginx 리버스 프록시</code><br>
        👎 http/https 서버 노드에서 직접 제어 <br>
        👍 노드는 http포트에서 작동, https트래픽은<br>
        Nginx에서 수신, 인증을 거쳐 노드로 프록시<br>
        Nginx, Apache등 프록시/로드밸런서 - HTTPS 핸들링<br>
        Node.js 애플리케이션 - 내부적으로 HTTP 핸들링<br>
        SSL 인증서 프록시에서 일원화 관리<br>
        리버스 프록시에서 리다이렉트/HSTS/보안 헤더.. 추가 설정 용이<br>
        여러개의 노드 앱을 하나의 엔드포인트로 통합관리<br>
        앱은 HTTP만 핸들링
      </td>
      <td></td>
    </tr>
    <tr>
      <td style="text-align: center">4</td>
      <td style="text-align: center">2025-04-17</td>
      <td style="text-align: center"><code>Linux</code><br><code>JS</code></td>
      <td>
        <code>방화벽</code><br>
        개발 편의를 위해 전개방 &gt; 방화벽 적용<br>
        http/https 포트 외에도 내외부 접근에 따라 포트(MySQL등) 개방<br>
        <code>Nginx 설정 방식</code><br>
        프록시 설정을 통한 통합 관리 및 세부 설정<br>
        <code>Unix vs TCP/IP</code><br>
        DBConnection → <code>localhost → 유닉스 소켓</code> <code>Domain/IP → TCP/IP</code><br>
        유닉스 소켓<br>
        네트워크 스택 비경유. 외부 노출 제한적, 고성능
      </td>
      <td></td>
    </tr>
    <tr>
      <td style="text-align: center">5</td>
      <td style="text-align: center">2025-04-18</td>
      <td style="text-align: center"><code>JS</code><br><code>Refactoring</code></td>
      <td>
        <code>Prisma ORM</code><br>
        기존 떙SQL → 프리즈마ORM<br>
        AI assistant 통해 변경시 한번에 전체 변경하기보단 단계적으로<br>
        DB 구조 뽑아서 스키마 생성<br>
        환경변수값 적용 후 클라이언트 테스트<br>
        테스트 성공 후 코드덩어리 분리 → 테스트<br>
        !Bigint형 BigInt.prototype.toJSON toString<br>
        Front_TODO_<br>
        <b>QnA Request Path 수정한거 반영</b>
      </td>
      <td></td>
    </tr>
    <tr>
      <td style="text-align: center">6</td>
      <td style="text-align: center">2025-04-21</td>
      <td style="text-align: center"><code>JS</code><br><code>Refactoring</code></td>
      <td>
        <code>Prisma</code> 에서 DISTINCT<br>
        <pre>
    // 문제 목록 조회
    static async getProblems() {
        // DISTINCT는 Prisma에서 groupBy로 대체
        const result = await await prisma.$queryRaw`SELECT DISTINCT problem_id FROM solve`;
        const problems = await prisma.solve.findMany({
            distinct: ['problem_id'],
            select: { problem_id: true }
        });
        return problems;
    }</pre>
      <code>Invalid value for argument `distinct`. Expected SolveScalarFieldEnum.</code><br>
      <pre>Prisma의 일부 버전(특히 5.x 이상)에서는 distinct에 문자열 배열이 아닌 
Enum만 허용하도록 타입이 강화된 사례가 있습니다.
JavaScript(.js) 환경에서도 내부적으로 Enum을 요구할 수 있으며, 
이 경우 문서와 실제 동작이 다를 수 있습니다.
Prisma 클라이언트가 생성될 때 모델의 모든 필드 Enum(SolveScalarFieldEnum)을 
자동 생성하는데,
JS에서는 이 Enum을 직접 import해서 쓸 수 없습니다.
공식적으로는 문자열 배열이 허용되어야 하지만,
Prisma 버전/환경에 따라 오류가 발생할 수 있습니다.
이 경우, Prisma를 TypeScript로 마이그레이션하거나,
distinct 대신 raw 쿼리로 대체하는 것이 현실적인 해결책입니다.</pre>
      Enum은 프리스마 스키마가 알아서 생성해준다고 하는데 TS에서만 쓴댄다 ?? > raw로 우회..<br>
      </td>
      <td></td>
    </tr>
    <tr>
      <td style="text-align: center" rowspan="2">7</td>
      <td style="text-align: center" rowspan="2">2025-04-28</td>
      <td style="text-align: center"><code>MySQL</code><br></td>
      <td>
        <code>View placeholder</code> <br>
        <pre>
DB에서 뷰를 생성시, 복합 참조 등의 경우에서 
아직 생성되지 않은 테이블이나 뷰를 참조, 
참조 무결성 오류 발생.

이에 Forwad Engineering / mysqldump 등
스키마 구조 export시 뷰의 정의 무결성 유지차(정의 안전하게 포함?)
뷰와 동일 구조의 placeholder table 임시 생성, 이후 대체
</pre>
      </td>
      <td></td>
    </tr>
<tr>
      <td style="text-align: center"><code>Java</code><br></td>
      <td>
        <code>Core Principles of Java</code> <br>
        <pre>생각나는대로
<hr/>
- 객채 지향
  - 코드 재활용성 향상
  - 역할/책임 분배에 따른 명확/직관적 제품 관리
  - 유지보수 용이
  - 라이브러리 방대화, 선순환에 따른 개발 효율성 증진
  - 클래스 / 제네릭 / 상속 / 구현 / 인터페이스 / 캡슐화 / 모듈화
- `JVM` / JRE / JDK  
  - 핵심은 JVM? JDK는 development kit 이고 re무슨 에디션으로 기억 
  - virtual machine이 가상환경에서 뭔가 돌리면서 뭔가 훌륭
  - garbage collection이 JVM에 있었다했던거같고
  - 멀티쓰레드도 얘가구현했었나
<hr/>
Perplexity
<hr/><table>
  <tbody>
  <tr>
  <td>특징</td><td>자바(Java)</td><td>과거 언어(C, C++, Pascal 등)</td>
  </tr>
  <tr>
<td>플랫폼 독립성</td>
<td>JVM 기반, Write Once Run Anywhere</td>
<td>OS/플랫폼별 별도 컴파일 필요</td><tr>
  <tr>
<td>객체지향</td>
<td>철저한 OOP, 클래스 기반</td>
<td>C: 절차지향, C++: 혼합</td></tr>
  <tr>
<td>자동 메모리 관리</td>
<td>자동(가비지 컬렉션)</td>
<td>수동(malloc/free 등)</td></tr>
  <tr>
<td>내장 보안/네트워크</td>
<td>내장 API 및 샌드박스, 안전성 강조</td>
<td>외부 라이브러리, 보안 취약</td></tr>
  <tr>
<td>멀티스레딩</td>
<td>언어/라이브러리 차원 지원</td>
<td>플랫폼별 구현 필요</td></tr>
  <tr>
<tr><td>동적 로딩</td>
<td>JVM이 지원</td>
<td>정적 링크 기본, 동적 라이브러리 복잡</td></tr>
  <tr>
<td>문법/생산성</td>
<td>안전성·생산성 중시, 현대적 기능 지속 도입</td>
<td>포인터 등 위험 요소, 최신 기능 도입 느림</td></tr>
  <tr>
<td>성능</td>
<td>JIT로 인터프리터 한계 극복</td>
<td>네이티브 컴파일, 실행 속도 빠름</td></tr>
  <tr>
<td>라이브러리/생태계</td>
<td>방대하고 강력</td>
<td>제한적, 외부 의존</td>
</tr>
  </tbody>
<tr>
<td>객체지향 프로그래밍</td>
<td>플랫폼 독립성[유연성?]</td>
<td>강한 타입 검사</td>
<td>견고함과 보안[샌드박스 환경?]</td>
</tr>
<tr>
<td>간결하고 익숙한 문법</td>
<td>자동 메모리 관리</td>
<td>멀티스레딩 지원</td>
<td>풍부한 표준 라이브러리</td>
</tr>
</table>
- OOP(Object oriented programming)
  - 객체Object-속성field-행위method 구성, 상호작용을 통해 솔루션 [인스턴스는?]
  - Core Principles of OOP 캡슐화/상속/다형성/추상화
  - C: 절차지향, 구조체 / C++: 다중상속, 포인터 / Java: 단일상속 제네릭
- JIT(Just-In-Time) 컴파일
  - 프로그램 실행 중 바이트코드를 기계어로 실시간 컴파일, 성능 최적화
  - 인터프리터가 바이트코드를 실행하면서 자주 호출되는 코드를 식별합니다.
  - JIT 컴파일러가 해당 코드를 네이티브 코드로 변환합니다.
  - 이후에는 컴파일된 코드를 직접 실행하여 성능을 향상시킵니다.
  - 간단하게는 자주쓰는코드의 효율적 실행이니까 이것도 나름의 객체화 아닌가
  - Strong : 정적 컴파일 대비 실생 환경에 최적화(CPU Architecture), HotSpot
  - Week : 초기 실행에 컴파일 지연, 메모리 사용량 증가.
  - Ex : JVM
- Structured Concurrency(구조화된 동시성)
  - 동시성 작업의 수명 주기를 코드의 구문 구조에 맞춰 관리
  - 부모 작업이 하위 작업 제어, 오류 전파/자원 정리 보장
  - ! Scope 내 제한 : 모든 동시성 작업은 명시적 스코프에서 생성/종료
  - Exception throw / try catch 구문들 + 그 구조들
  - 하위 작업 실패 시 부모 작업으로 예외 전파
  - 스코프 종료 시 파일 핸들, 네트워크 연결 등 안전 해제 보장
  - 데드락 감소 : 작업 간 종속성을 코드 구조로 명시화
    - 데드락 문제가 종속성 명시로 해결이 가능한 부분이구나?
  - 스레드 누수 방지 : 스코프 외부 작업 제한으로 누수 방지
  * 정해진 문?법을 활용함으로써 효율적 코딩과 효과적인 자원 관리, 이벤트 핸들링 가능
- Enterprise Computing(기업?조직?비즈니스? 컴퓨팅)
  - 대규모 조직 복잡 비즈니스 프로세스 지원용 컴퓨팅 인프라/소프트웨어 체계
  - 주요 구성 요소
    - ERP(Enterprise Resource Planning) : 부서별 데이터 통합관리
    - CRM(Customer Relationship Management) : 고객별 데이터 분석/판매 자동화
    - Cloud Computing : AWS / Azure [Saas] 등 확장성[통일성, 경량] 있는 인프라
    - 빅데이터 분석 : Hadoop, Spark 활용 대량 데이터 처리
  - 핵심 특징
    - 고가용성 / 보안 / 통합
    - 통합에서 RESTful API, Enterprise Service Bus 활용 시스템 연동
- Distributed Systems(분산 시스템) : 여러 컴퓨터가 네트워크로 연결, 단일 시스템처럼 동작하는 컴퓨팅 환경.
  - 주요 특징
    - 확장성: 노드(서버 등) 추가를 통해 처리 용량 증설.
    - 내결함성: 일부 노드 장애 시에도 시스템 전체는 운영.
    - 병렬 처리: MapReduce 등으로 대용량 데이터 분산 처리.
  - 아키텍처 유형
    - 클라이언트-서버: 중앙 서버가 요청을 처리.
    - P2P(Peer-to-Peer): 모든 노드가 동등 역할 수행.
    - 마이크로서비스: 독립적인 서비스가 API로 통신.
  - 기술 사례
    - 분산 데이터베이스: Cassandra, MongoDB.
    - 분산 파일 시스템: HDFS, Google File System.
    - 메시징 시스템: Kafka, RabbitMQ.
  - 발전 과제
    - 일관성 유지: CAP 이론에 따라 Availability와 Consistency 간 균형 필요.
    - 네트워크 지연: 분산 트랜잭션 관리가 복잡합니다.
- Virtualize(가상화)
<table>
<tr>
<td>구분</td>
<td>전통적 가상화(VM)</td>
<td>컨테이너 기반(Docker)</td>
</tr>
<tr>
<td>추상화 계층</td>
<td>하드웨어 계층(Hypervisor 사용)</td>
<td>OS 커널 계층(호스트 커널 공유)</td>
</tr>
<tr>
<td>실행 단위</td>
<td>전체 OS + App</td>
<td>App + 의존성 패키지</td>
</tr>
<tr>
<td>성능</td>
<td>오버헤드 ↑(Guest OS부팅 필요)</td>
<td>오버헤드 ↓(ms단위 실행)</td>
</tr>
<tr>
<td>리소스 사용</td>
<td>각 VM이 독립적 메모리/CPU 할당</td>
<td>호스트 리소스 공유 및 동적 할당</td>
</tr>
<tr>
<td>이식성</td>
<td>호환성 제한(VM 이미지 크기↑</td>
<td>Docker 호환 환경 동일 실행</td>
</tr>
<tr>
<td>부팅 시간</td>
<td>1~5분</td>
<td>~1초</td>
</tr>
<tr>
<td>디스크/메모리</td>
<td>GB / Guest OS 메모리</td>
<td>MB / 프로세스 메모리</td>
</tr>
<tr>
<td>호환성</td>
<td>모든 OS 독립적 실행?</td>
<td>Linux / Windows 컨테이너 분리</td>
</tr>
</table>
</pre>
      </td>
      <td></td>
    </tr>
    <tr>
      <td style="text-align: center">8</td>
      <td style="text-align: center">2025-05-07</td>
      <td style="text-align: center"><code>CS</code><br></td>
      <td>
        <code>Various</code> <br>
        <pre>

Endpoint
-
    - URL. 마지막/끝단.
    - 요청과 응답의 상호작용 위치. 특정 기능/데이터와 1:1 대응
    - 메소드와 함께 사용, 메소드는 리퀘스트 패킷에 들어있나
Mock
-
    - 가짜/임시 함수. 테스트 과정에서 외부 의존성 등 
      실행의 복잡도나 지연시간을 증가시키는 함수를 가짜로 구현, 핵심 로직만 테스트 가능하도록
Stub
-
    - 임시로 대체한 미완성부
    - 미구현된 DB에 데이터 DML 실행 등
CI, Continuous Integration
-
    - 지속적 코드||구조의 통합/테스트/검사/디버깅
CD, Continuous Delivery/Deployment
-
    - 지속적 테스트+배포준비/배포
SI, System Integration
-
    - 시스템 통합. 각 구성품을 통합/연결해 하나의 큰 시스템으로 구축 및 운영
DevOps, Development+Operations
-
    - 개발+운영 분야간의 협업, 통합 등 
      전반적/전체적인 조직 문화, 프로세스, 도구, 역할 등을 통칭
    - 통합적 업무를 통해 사용자에게 빠르고 안정적인 소프트웨어 제공
Jest
-
    - coverage report: stmts/branch/funcs/lines/uncovered line
      [실행 가능 문장|명령] [코드 라인] 대부분 한줄에 명령문 한개니 비슷
      우테코 코딩 컨벤션에서 강조한 이유가 따로있나
</pre>
      </td>
      <td></td>
    </tr>
    <tr>
      <td style="text-align: center">9</td>
      <td style="text-align: center">2025-05-08</td>
      <td style="text-align: center">
<code>CS</code><br>
<code>Node.JS</code><br></td>
      <td>
        <code>Var</code> <br>
        <pre>

보일러플레이트
-
    - 활자판? 반복적으로 찍어내듯이 작성하는, 필요하지만 별도의 로직이나 구조 변경 없이 작성해야 하는 코드
    - 반복되는 만큼 표준이자 기본이라 볼 수 있되, 굳이 반복할 필요는 없으니 어노테이션과 도구(Lombok) 이용해 불필요 작업 방지
아티팩트 종속성
-
    아티팩트 : 라이브러리 클래스 등 객?체? 
    요약 : 소프트웨어 개발 과정에서 만들어지는 모든 산출물.
    정의 : 아티팩트는 소프트웨어의 아키텍처, 설계, 기능을 설명하거나 구현하는 데 사용되는 부산물로, 
           개발자가 전체 개발 프로세스를 추적하고 유지보수하는 데 중요한 역할을 합니다.
    용례
        코드 아티팩트 - jar, war, 소스 코드, 테스트 스크립트, 로그 파일 ...
        문서 아티팩트 - 설계 문서, 회의록, 메뉴얼, 다이어그램, 데이터 모델 ...
        프로젝트 관리 아티팩트 - 프로젝트 로드맵, 변경 로그, 품질 계획서 ...
    중요성
        재현성 - 동일 소스 코드로 동일 아티팩트 재생성/재현 
        이식성 - 하나의 아티팩트를 다양한 환경에 배포
        추적 가능성 - 특정 소스 코드 버전과 연결된 아티팩트 식별/추적
        자동화 지원 - CI/CD 파이프라인에서 배포 자동화 핵심 요소
    아티팩트들 잘 모으고있었고
API
=
    Application Programming Interface
    두 소프트웨어 구성 요소가 서로 
        통신하도록 해 주는 매커니즘.
        상호작용할 수 있게 해주는 매개체 = 인터페이스
    req/res 통신의 명확한 방식. 규약
</pre>
        <code>백준 코테</code> <br>
        <pre>

IO
=
    // 백준에서 Node 쉽지않고
    const fs = require('fs');
    const filePath = process.platform === "linux" ? "/dev/stdin" : "../input.txt";
    const input = fs.readFileSync(filePath, 'utf8').toString().trim().split('\n');
    백준도 리눅스였넹
아니 노드로보는게 맞나 TS쓰는게정상아닌가 ㅅㅂ
</pre>
      </td>
      <td></td>
    </tr>
    <tr>
      <td style="text-align: center">10</td>
      <td style="text-align: center">2025-05-09</td>
      <td style="text-align: center"><code>C?S</code><br></td>
      <td>
        <code>CallBack</code> <br>
        <pre>재귀문 > 반복문</pre>
      </td>
      <td></td>
    </tr>
    <tr>
      <td style="text-align: center"></td>
      <td style="text-align: center">2025-05-26</td>
      <td style="text-align: center"><code>React</code><br></td>
      <td>
        <code>React Structure</code> <br>
        <pre>

Flux Pattern
=
    Def)    페이스북(메타)에서 제안한 React 앱의 상태 관리 패턴.
            단방향 데이터 흐름이 핵심
            주요 구성요소 : Action > Dispatcher > Store > View(React Component)

    Struc)  Action
            사용자의 인터렉션(클릭 등)이나 네트워크 이벤트 등에서 발생.
            {type: 'ADD_TODO', payload: ...} 형태의 객체
            Dispatcher 
            모든 액션을 받아서 스토어로 전달하는 중앙 허브
            여러 스토어가 있을 경우 액션을 분배
            Store
            실제 어플리케이션의 상태(state) / 비즈니스 로직을 보관
            액션을 받아서 상태를 변경
            뷰에 변경 이벤트(emit change)를 알림
            View
            스토어의 상태를 구독(감지)하고, 상태가 변경되면 리렌더링
            사용자의 입력을 액션으로 변환해 Dispatcher에 전달
            useState(함수형 컴포넌트) / setState(클래스형 컴포넌트)
            state는 컴포넌트 안에서만 관리되고, 값이 바뀌면 해당 컴포넌트가 리렌더링됨
            
    Feat)   Features / Characteristics
            Store 직접 접근 금지
            상태 변경은 반드시 Action > Dispatcher > Store 경로를 통해서만
            단방향 데이터 흐름
            상태가 변경되면 View 리렌더링, View에서 직접 Store를 수정 불가.

Redux Library
=
    Def)    Flux의 아이디어를 더 단순화한 상태 관리 라이브러리
            Store는 단 하나
            Reducer라는 순수 함수로  상태 변화 정의
    Struc)  Action      - { type : 'INCREMENT', payload : ... } 등의 인터렉션 등
            Dispatch    - 액션을 스토어에 전달
            Reducer     - 이전 상태와 액션을 받아서 새로운 상태를 반환하는 순수 함수
            Store       - 상태를 보관, 구독자(View)에게 상태 변경 알림
            View        - 상태를 구독(감지), 액션을 디스패치
    Feat)   Store 직접 수정 불가
            Reducer 통해서만 상태 변경
            불변성 유지
            상태 객체를 직접 수정하지 않고, 새로운 객체로 반환
            단방향 데이터 흐름
            Action > Dispatch > Reducer > Store > View

Two-way Binding(양방향 바인딩)
=
    Def)    묶여있다 / 양방향으로
            데이터(Model) / 화면(UI, View)이 상호 연결되어 있어
            둘 중 하나가 변경되면 자동으로 나머지 하나가 동기화되는 데이터 처리 방식
            코드/데이터의 값이 변경되면 UI/뷰에도 즉시 반영되고
            뷰에서 사용자가 값을 바꾸면 모델에도 즉시 반영 
            Ex) Vue.js / Angular / Svelte ...
            React는 기본적으로 단방향 바인딩이지만
            상태(state)/이벤트핸들러 조합시 유사하게 구현 가능

One-way Binding(단방향 바인딩)
=
    Def)    상태 관리 컴포넌트에서 자식 컴포넌트에 props로 값을 넘기고,
            변경 이벤트를 콜백으로 받아 상태를 갱신하는 식으로 구현

</pre>
<code>Reflect API</code> <br/>
<pre>

### 프로그래밍 언어에서 런타임이 객체/클래스/함수/속성 등
### 구조와 정보를 동적으로 조회하거나 조작할 수 있게 해주는 기능
JS(ES6) Reflect API
=
    Def)    ECMAScript 2015에서 도입된 내장 객체.
            객체의 속성 조회/수정/함수 호출 등 다양한 메타프로그래밍 작업을 위한 정적 메소드 제공.
            객체의 내부 동작을 직접 다루거나 Proxy와 함께 사용
    Method) Reflect.get      (obj, prop)            : 속성값 접근
            Reflect.set      (obj, prop)            : 속성값 설정
            Reflect.has      (obj, prop)            : 속성값 존재유무 확인
            Reflect.apply    (func, thisAlg, args)  : 속성값 함수 호출
            Reflect.construct(constructor, args)    : 생성자 호출. ( == new )

Java Reflect API
=
    날아감ㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋ

</pre>
      </td>
      <td></td>
    </tr>
    <tr>
      <td style="text-align: center">10</td>
      <td style="text-align: center">2025-05-28</td>
      <td style="text-align: center"><code>Algorithm</code><br></td>
      <td>
        <code>Greedy, 최소 불가능 합 판별</code> <br>
        <pre>

## Function
#### 1. 배열 정렬: 숫자를 오름차순으로 정렬합니다.
#### 2. 현재까지 만들 수 있는 최대값 추적: current_max 변수를 0으로 초기화합니다.
#### 3. 순회 및 검증:
> 각 숫자를 순회하며, 현재 숫자가 current_max + 1보다 크면
current_max + 1이 만들 수 없는 최소값입니다.
>
>그렇지 않으면 current_max에 현재 숫자를 더합니다.
>
#### 4. 모든 숫자 처리 후: 모든 숫자를 처리했다면 current_max + 1을 반환합니다.
## Complexity
<img src="https://velog.velcdn.com/images/nn98/post/2fe6eff6-eb53-4d5b-b3e5-7838e9373853/image.png"/>

## 해?석
#### 판별 숫자/재료 숫자로 호칭, 판별 숫자는 1(0+1)부터 시작<br />재료 숫자가 판별 숫자보다 클 경우 그 판별 숫자가 최소 불가능 합<br />재료 숫자가 판별 숫자보다 작거나 같으면 재료 숫자 += 판별 숫자
#### 재료 숫자를 하나씩 더한 수+1을 못만들면 그게 최소 불가능 합
</pre>
      </td>
      <td></td>
    </tr>
    <tr>
      <td style="text-align: center">11</td>
      <td style="text-align: center">2025-07-02</td>
      <td style="text-align: center"><code>CS</code><br><code>JS</code><br></td>
      <td>
        <code>Map, Object</code> <br>
        <pre>

## Object의 정렬
#### ES6부터 Object의 key가 문자열일때만 순서가 보장된다
</pre>
`TO?DO`

뭔 얘기일지 확인하고 해보기
1. 시스템 콜렉션 타입을 골고루 활용하기
2. 디렉토리 반복 매칭 구현하기
      </td>
      <td></td>
    </tr>
    <tr>
      <td style="text-align: center">12</td>
      <td style="text-align: center">2025-07-07</td>
      <td style="text-align: center"><code>CS</code><br><code>AI</code><br></td>
      <td>
        <code>MCP</code> <br>
        <pre>

# Model Context Protocol
## 개념 정의
### 인공지능(특히 대형 언어 모델LLM)과 외부 데이터 소스/도구를 표준 방식으로 연결하는 개방형 프로토콜
## 아키텍처
- ### Host : LLM App(IDE, ChatBot etc), 여러 클라이언트 관리, 사용자 인증/컨텍스트 집계
- ### Client : Host 와 Server 사이 1:1 연결, 메시지 라우팅, 기능 협상
- ### Server : 외부 데이터/툴 제공자, 실제 작업(검색, 파일 접근 등) 수행
- ### Protocol : JSON-RPC 2.0 기반 메시지 포맷, 연결/협상/구독/오류 처리 등 정의
### `메시지 흐름 및 구조`
- 하단 JSON-RPC 2.0 포맷 참고
## 주요 목적
### AI가 다양한 데이터/파일/시스템/툴 과 쉽게 연동할 수 있도록 통합 인터페이스 제공
## 적용 예시
- ### AI 데스크톱 앱(Calude Desktop etc)에서 파일 시스템 접근
- ### 개발환경(IDE)에서 코드/문서/데이터 연동
- ### 기업 내부 지식베이스, CRM, 데이터페이스 등과 AI의 통합
## 기술 특징 "AI의 USB-C"
- ### JSON-RPC 2.0기반 메시지 전송
- ### 서버-클라이언트 구조(MCP 서버, MCP 클라이언트, MCP 호스트)
- ### LSP와 유사 구조
## 주요 사례
- ### Anthropic, OpenAI, Google DeepMind 등 주요 AI 기업 및 다양한 개발 도구들이 MCP 채택
## 장점
- ### 단일 표준(plug-and-play)로 다양한 데이터·툴 연동
- ### 보안·접근 제어, 기능 협상, 오류 처리 등 내장
- ### 각종 AI 앱, IDE, 챗봇 등에서 손쉽게 확장 가능

</pre>
<code>JSON-RPC 2.0</code> <br>
<pre>

## 네트워크를 통한 PRC를 위해 설계된 프로토콜
#### 경량, 상태 비저장(stateless) 프로토콜, JSON 포맷 사용, HTTP, WebSocket 등 다양한 전송 계층에서 동작
#### Request 구조
- 클라이언트가 서버로 원격 함수 호출을 요청하는 메시지.
    - jsonrpc : 프로토콜 버전(항상 2.0)
    - method : 호출 함수명
    - params : 함수 인자
    - id : 요청 식별자(Response 매칭)
#### Response 구조
- 서버가 클라이언트의 요청에 대한 결과를 반환하는 메시지.
    - jsonrpc : 상동
    - result : 함수 실행 결과
    - error : 함수 실행중 오류 발생 시 오류 객체
    - id : 요청 식별자와 매칭해 동일한 값
#### Notification(알림)
- 식별자(id) 없이 응답 불필요한 단방향 메시지.

- ### 명시된(Named) 매개변수(Parameters)
    - "인자"를 객체로 전달 가능(가독성 / 확장성). 근데 원래 JSON도 가능했는데;
- ### 표준화된 오류 처리
    - 오류 코드 / 메시지 형식이 명확히 정의.
- ### 일괄(Batch) 요청
    - 복수 요청을 한 번에 전송

## PRC
### Remote Procedure Call
원격 프로시저 호출.
</pre>
<code>LSP</code> <br>
        <pre>

## 코드 에디터(클라이언트) - 언어 서버(서버)간 통신을 표준화한 프로토콜
- #### 코드 자동완성, 오류 진단, 정의 - 사용 위치 이동 등 언어 인텔리전스 기능 에디터에서 일관 제공
- #### 언어 서버 - 각 프로그래밍 언어별로 문법분석/자동완성/오류진단 등 기능 제공 독립 프로세스
- #### 클라이언트 - VSCode / Vim / Eclipse / IntelliJ etc.. LSP 지원 에디터 / IDE
- #### LSP Message - JSON-RPC 2.0 Format으로 textDocument/[didOpen/didChange/definition] 다양한 메시지 송수신
- #### 구조/흐름
    - 에디터가 파일을 열거나 변경 - LSP 클라이언트가 서버에 알림 전송
    - 서버는 코드 분석 - 진단 결과 / 자동완성 후보 / 정의 위치 등 정보 응답
    - 클라이언트는 응답 수신 후 에디터 UI에 반영
### 장점
- 언어 서버 하나로 다양한 에디터 지원 가능
- 에디터 - 서버 간 표준화된 인터페이스로 확장성 우수
</pre>
      </td> 
      <td></td>
    </tr>
  </tbody>
</table>
</details>
</h3>

# Half 

<h3> <details> <summary> 2025 - 07 ~ </summary>

<table>
<thead>
<tr>
<th>순번</th>
<th>001</th>
</tr>
</thead>
<tbody>
<tr>
<th>
날짜
</th>
<th>
2025-07-10
</th>
</tr>

<tr>
<th>
주제
</th>
<th>
<h4> <code>Java Spring_Boot/_MVC</code> </h4>
</th>
</tr>

<tr>
<th>
내용
</th>
<td>

![image](https://github.com/user-attachments/assets/cbf7f0b3-7cc4-44e6-a0ec-51a82f0e3379)
# Spring
자바 기반 오픈 소스 프레임워크  
객체의 생성/소멸/의조선 관리 등 복잡한 작업 대리  
개발자는 비즈니스 로직에 집중  
- **IoC (Inversion of Control, 제어의 역전)**
  - 객체의 생성 및 생명주기 관리를 컨테이너(스프링)가 담당
- **DI (Dependency Injection, 의존성 주입)**
  - 객체 간 의존 관계를 외부에서 주입
- **Bean (빈)**
  - 스프링 컨테이너에 의해 관리되는 객체
- **Bean Factory**
  - 스프링에서 IoC를 담당하는 기본 컨테이너
- **ApplicationContext**
  - BeanFactory의 확장, 더 많은 부가 기능(메시지, 이벤트) 제공
- **AOP (Aspect Oriented Programming, 관점 지향 프로그래밍)**
  - 공통 관심사 분리-코드 중복을 감축, 
    유지보수 용이화 프로그래밍 패러다임

# Spring Boot
스프링을 더 쉽고 빠르게 사용할 수 있도록 보조하는 도구이자 프레임워크  
- 자동 구성 (Auto-configuration)
  - 프로젝트에 포함된 라이브러리 기반 필요 설정 자동 수행
- 스타터 (Starter)
  - 특정 기능 추가 용이하도록 묶인 의존성 패키지`spring-boot-starter-web`
- 내장 서버 (Embedded Server)
  - 톰캣, 제티, 언더토우 등 WAS 내장 / 서버 설치 없이 실행
- 의존성 관리 (Dependency Management)
  - Maven, Gradle 등 빌드 도구를 통해 필요 라이브러리 관리
- 초기화 도구 (Spring Initializr)
  - 웹 기반 프로젝트 생성 도구, 필요 의존성 선택-스프링부트 프로젝트 시작 용이

# Spring MVC
웹 애플리케이션 개발을 위한 모듈, MVC 패넡 지원
- MVC Pattern
  - Model: 비즈니스 로직 및 데이터 처리
  - View: 사용자에게 보여지는 화면(HTML, JSON, etc..)
  - Controller: 사용자의 요청을 받아 모델에서 처리, 뷰로 전달
- DispatcherServlet
  - 모든 요청을 받아 적절한 컨트롤러에 분배하는 프론트 컨트롤러 역할
- HandlerMapping
  - URL 등 요청 정보를 기반으로 어떤 컨트롤러가 처리할지 결정
- HandlerAdapter
  - 컨트롤러를 실제로 실행시켜주는 어댑터 역할
- ViewResolver
  - 논리적 뷰 이름을 실제 뷰(JSP, Thymeleaf)로 변환
- ModelAndView
  - 컨트롤러가 반환하는 객체, Model데이터 / View정보 포함
- @Controller, @RestController, @ReqeustMapping
  - 각종 어노테이션을 통해 컨트롤러 및 요청 매핑을 정의
</td>
</tr>

</tbody>
</table>

<table>
<thead>
<tr>
<th>순번</th>
<th>001</th>
</tr>
</thead>
<tbody>
<tr>
<th>
날짜
</th>
<th>
2025-07-10
</th>
</tr>

<tr>
<th>
주제
</th>
<td>
<code></code>
</td>
</tr>

<tr>
<th>
내용
</th>
<td>
2025-07-10
</td>
</tr>

</tbody>
</table>

</details>
</h3>

* * *
<h1> `舊`CS 정리 </h1>

* * *
<h2> 테마별 </h2>

<details>
<summary><i><b>General</b></i></summary>


</details>

<details>
<summary><i><b>Java</b></i></summary>


</details>

<details>
<summary><i><b>JS</b></i></summary>


</details>

<details>
<summary><i><b>DB</b></i></summary>


</details>

<details>
<summary><i><b>Server</b></i></summary>

- Image<sup>[1](#이미지)</sup>: 일반적으로 운영체제와 애플리케이션 소프트웨어 등을 포함한 완전한 실행 환경을 특정 상태로 캡처한 정적인 파일

</details>

<h2> 일자별 </h2>

<details><summary><i><b>2023</b></i></summary>

 <details><summary>06/16</summary>

- Chat GPT3.5 중간에 끊기던거 continue generate 기능
- 서버 코드 테스트: Docker / VM / etc...
- Docker Hyper-V WSL(Windows Subsystem for Linux)
- Image<sup>[1](#이미지)</sup>: 일반적으로 운영체제와 애플리케이션 소프트웨어 등을 포함한 완전한 실행 환경을 특정 상태로 캡처한 정적인 파일
- [[Windows 10] Docker 설치 완벽 가이드(Home 포함)](https://www.lainyzine.com/ko/article/a-complete-guide-to-how-to-install-docker-desktop-on-windows-10/)
  </details>
  <details>
  <summary>06/20</summary>

    - Docker
        - Docker : 컨테이너 기반의 오픈소스 가상화 플랫폼
            - Container
                - 독립된 가상 곤간에서 프로세스가 동작하는 기술
                - 1서버 - n컨테이너
                - 프로그램, 실행환경 추상화, 동일 인터페이스 제공 <br> 프로그램 배포/관리 단순화
                - 독립/연동 실행 자유
                - 가상 머신: 각 가상 머신에 자원 할당 및 운영체제 구축 필요 <br> 컨테이너 기반 가상화: 도커 엔진 위에서 동작, 필요 자원
                  활용 <br> ![구조 비교](https://blog.kakaocdn.net/dn/mE4qK/btr1EcLMZMg/qGN0wmhM9qKjPqVoGiYKG1/img.png)
        - Docker Image
            - 소스 코드/실행에 필요한 툴/파일/라이브러리/설정값 등 포함
            - 같은 이미지에서 여러개의 컨테이너 생성 가능, <br> 컨테이너의 상태가 바뀌거나 삭제되더라도 이미지는 변하지 않음
            - Docker Image는 Docker Hub에 업로드, 공유/다운 가능
        - Docker File
            - Docker Image 생성용 파일
            - 생성할 이미지 정보 기술
            - Docker File 열람을 통해 이미지 구성 파악
        - [설치](https://www.lainyzine.com/ko/article/a-complete-guide-to-how-to-install-docker-desktop-on-windows-10/)
        - [테스트](https://www.lainyzine.com/ko/article/a-complete-guide-to-how-to-install-docker-desktop-on-windows-10/)
            - 도커 vm 실행 확인 <br> wsl -l -v
            - 리눅스 버전 확인 <br> wsl -d docker-desktop busybox
            - 도커 버전 확인 <br> docker version
            - 실행중인 컨테이너 확인 <br> docker ps
            - 최신버전의 nginx 이미지 기반 컨테이너 생성/싱행 <br> docker run -p 4567:80 -d nginx:latest <br> [결과 확인](127.0.0.1:4567)
              호스트 포트:컨테이너 포트

      </details>
      <details>
        <summary>06/23</summary>

        - WSL`GPT IS GOD`
            - Ubuntu
                - MS Store에서 설치
                - 설치된 앱을 실행 || cmd 등에서 wsl -d Ubuntu 실행
                - __Shift+Insert__ 안먹음; 우클릭으로 붙여넣기 가능
                - __Nginx__ 수정했으면 꼭 재시작
                - iptables
                    - `!ERR` sudo iptables -I INPUT 5 -i ens3 -p tcp --dport 9818 -m state --state NEW,ESTABLISHED -j
                      ACCEPT
                    - `!ERRMSG` iptables: Index of insertion too big.
                    - `!SOL`sudo iptables -A INPUT -i ens3 -p tcp --dport 9818 -m state --state NEW,ESTABLISHED -j
                      ACCEPT
      </details>
      <details>
        <summary>06/28</summary>

        - Ubuntu
            - Symbolic Link
                - *윈도우의 바로가기 개념? 참조값?*
                - !https용 pem 파일 복사/압축/압축해제/이동 등 작업 시도했더니 관련 오류 발생
                - `심볼릭 링크를 생성할 수없습니다` `cannot operate on dangling symlink`
                - 권한문제인줄 알았더니 심볼릭링크문제
                - letsencrypt key 파일이 자동 갱신될때마다 아카이브 폴더에 새로운 pem 파일 생성.
                - 생성된 최신 파일을 참조하는 pem 파일을 프로젝트에서 사용
      </details>
</details>

[//]: # (<details>)

[//]: # (  <summary>년</summary>)

[//]: # (  이 부분은 년에 대한 내용입니다.)

[//]: # ()

[//]: # (  - <details>)

[//]: # (    <summary>월</summary>)

[//]: # (    이 부분은 월에 대한 내용입니다.)

[//]: # (    )

[//]: # (    - <details>)

[//]: # (      <summary>일</summary>)

[//]: # (      이 부분은 일에 대한 내용입니다.)

[//]: # (    </details>)

[//]: # (    )

[//]: # (    - <details>)

[//]: # (      <summary>일</summary>)

[//]: # (      이 부분은 일에 대한 내용입니다.)

[//]: # (    </details>)

[//]: # ()

[//]: # (  </details>)

[//]: # (</details>)
* * *
* * *
[1](이미지)
> 서버에서의 이미지는 일반적으로 운영체제와 애플리케이션 소프트웨어 등을 포함한 완전한 실행 환경을 특정 상태로 캡처한 정적인 파일입니다. 이 이미지를 사용하여 서버를 설정하고 배포할 수 있습니다.<br>
서버 이미지는 서버의 운영체제, 소프트웨어 패키지, 라이브러리, 환경 설정 등을 포함하며, 이를 기반으로 서버를 구성하고 실행할 수 있습니다. 이미지는 일반적으로 가상화 기술이나 컨테이너화 기술을 사용하여 만들어지며, 도커 이미지는 가장 일반적으로 사용되는 서버 이미지 형식 중 하나입니다.<br>
서버 이미지를 사용하면 개발 환경, 테스트 환경, 프로덕션 환경 등에서 동일한 실행 환경을 구성할 수 있습니다. 또한, 이미지를 쉽게 공유하고 배포할 수 있으며, 확장성과 유연성을 제공하여 서버 인스턴스를 신속하게 생성하고 관리할 수 있습니다.<br>
서버 이미지는 클라우드 플랫폼이나 가상화 기술에 따라 다양한 형식과 관리 방법이 있을 수 있습니다. 예를 들어, Amazon Web Services(AWS)에서는 Amazon Machine Image(AMI)를 사용하고, Google Cloud Platform(GCP)에서는 Compute Engine 이미지를 사용합니다.