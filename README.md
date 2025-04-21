# TIL
* * *
<style>
  .center { text-align: center; }
</style>
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
      <td class="center">1</td>
      <td class="center">2025-04-08</td>
      <td class="center"><code>JS</code></td>
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
      <td class="center">2</td>
      <td class="center">2025-04-11</td>
      <td class="center"><code>Alg</code></td>
      <td>
        <code>그래프</code><br>
        BFS-큐에 depth 1 넣고 빌때까지<br>
        DFS-스택[Stack Segment]이나 재귀<br>
        객체 사용용도에 따른 hashCode/equals 재정의
      </td>
      <td></td>
    </tr>
    <tr>
      <td class="center">3</td>
      <td class="center">2025-04-16</td>
      <td class="center"><code>JS</code><br><code>Refactoring</code></td>
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
      <td class="center">4</td>
      <td class="center">2025-04-17</td>
      <td class="center"><code>Linux</code><br><code>JS</code></td>
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
      <td class="center">5</td>
      <td class="center">2025-04-18</td>
      <td class="center"><code>JS</code><br><code>Refactoring</code></td>
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
      <td class="center">6</td>
      <td class="center">2025-04-21</td>
      <td class="center"><code>JS</code><br><code>Refactoring</code></td>
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
      <pre>Prisma의 일부 버전(특히 5.x 이상)에서는 distinct에 문자열 배열이 아닌 Enum만 허용하도록 타입이 강화된 사례가 있습니다.
JavaScript(.js) 환경에서도 내부적으로 Enum을 요구할 수 있으며, 이 경우 문서와 실제 동작이 다를 수 있습니다.
Prisma 클라이언트가 생성될 때 모델의 모든 필드 Enum(SolveScalarFieldEnum)을 자동 생성하는데,
JS에서는 이 Enum을 직접 import해서 쓸 수 없습니다.
공식적으로는 문자열 배열이 허용되어야 하지만,
Prisma 버전/환경에 따라 오류가 발생할 수 있습니다.
이 경우, Prisma를 TypeScript로 마이그레이션하거나,
distinct 대신 raw 쿼리로 대체하는 것이 현실적인 해결책입니다.</pre>
      Enum은 프리스마 스키마가 알아서 생성해준다고 하는데 TS에서만 쓴댄다 ?? > raw로 우회..<br>
      </td>
      <td></td>
    </tr>
  </tbody>
</table>
