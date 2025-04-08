# TIL
* * *
|순번|날짜|구분|내용|코드/참고|
|--|--|--|--|--|
|1|2025-04-08|`JS`|`패키지 설치 및 관리`<br>누더기 코딩의 대가<br>- 글로벌 패키지 남발<br>- 리액트 네이티브 초기화시 오류<br>_`TypeError: cli.init is not a function`_<br> 네이티브 구버전(안씀) 잔존<br>- dependency 관련 오류<br>- 네이티브 관련 패키지 재설치<br>- node npm nvm 업데이트<br><br>하루죙일해서 딲 프로젝트 빌드까지|<details><summary>Perplexity</summary>`npx react-native start --reset-cache` <br>`npm uninstall -g react-native-cli` <br>`npm uninstall -g react-native` <br>`npm uninstall -g @react-native-community/cli` <br>`npm cache clean --force` <br>`npm install --force react-native-cli react-native` <br>`npm install --save-dev @react-native-community/cli` <br>`npm install --save-dev @react-native-community/cli-platform-android` <br>`npm install --save-dev @react-native-community/cli-platform-ios` <br>`npx react-native start --reset-cache` <br>`npx rnx-align-deps --requirements react-native@0.76 --write`</details>|
||||||
