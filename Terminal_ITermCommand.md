# Terminal and ITerm Command

```bash
$ 명령어 [옵션명] [경로명]
```
- 명령어: 프롬프트에 전달하는 명령어, 명령어에 따라 옵션명의 작동방식이 달라진다.

- 옵션명: 명령어를 실행할 때 추가적으로 요구하는 옵션이다.

- 경로명: 절대경로, 상대경로로 표시할 수 있다. 없을 경우는 default 현재 경로이다.
***
```bash
$pwd
```
Print Working Directory

현재 자신이 어느 디렉토리에 위치하는 지 출력한다.
***
```bash
$cd 경로명
```
Change Directory

디렉토리(경로)를 변경한다. 경로를 표현하는 방식은 절대경로와 상대경로가 있다.

많이 이동하는 디렉토리에 대해서 정리한다.

example)
```bash
// 최상위 (루트) 디렉토리로 이동
$cd /

// 사용자의 홈 디렉토리로 이동
$cd ~

// 사용자의 Desktop(바탕화면) 디렉토리로 이동
$cd ~/Desktop
```
***
```bash
$ls [옵션명] [경로명]
```
List Segement

경로의 구성요소(파일, 디렉토리)를 나열한다.

example)
```bash
// 현재 경로 하위 파일/디렉토리 나열
$ls

// 현재 경로 하위 파일/디렉토리 자세한 정보(사용권한, 소유자, 그룹, 크기, 날짜 등)와 함께 나열
$ls -l

// 명시한 경로의 하위 파일/디렉토리 나열
$ls -l /test/exampleDir
```
***
```bash
$cp [원본파일] [대상파일]
$mv [원본파일] [대상파일]
```
CoPy / Move

원본파일을 대상파일로 복사한다 / 이동한다

파일을 가리킬 때에는 파일경로+이름으로 명시한다. (바이너리는 알 수 없으므로)

cp, mv는 기본적으로 파일을 다루는 명령어이며, 디렉토리를 처리할 때는 -r 옵션을 붙여준다. 

example)
```bash
// /test 디렉토리의 exampleFile 파일을 /newTest 디렉토리로 복사/이동
$cp /test/exampleFile /newTest/exampleFile
$mv /test/exampleFile /newTest/exampleFile

// /test 디렉토리의 exampleFile 파일이나 exampleDir 디렉토리를 /newTest 디렉토리의 exampleDir 디렉토리로 복사/이동
$cp -r /test/exampleFile /newTest/exampleDir
$mv -r ./test/exampleDir ./newTest/exampleDir
```
***
```bash
$touch 생성할파일명
$mkdir 생성할경로명
```
Touch / MaKe DIRectory

파일을 / 디렉토리를 생성한다.

example)
```bash
// /test 디렉토리에 exampleFile 이름의 빈 파일 생성
$touch /test/exampleFile

// /test 디렉토리에 exampleDir 이름의 빈 디렉토리 생성
$mkdir /test/exampleDir
```
***
```bash
$rm 지울파일명
$rmdir 지울경로명
```
ReMove / ReMoveDIRectory

파일을 / 디렉토리를 삭제한다.

example)
```bash
// /test 디렉토리의 exampleFile을 삭제
$rm /test/exampleFile

// /test 디렉토리의 exampleDir 디렉토리를 삭제
$rm -rf /test/exampleDir
$rmdir /test/exampleDir
```
***

```bash
Other Tip!
```
<Tab> 키를 클릭하면 현재 경로에 포함된 파일, 디렉토리의 이름을 자동완성시킬 수 있다.

특수기호를 통해 여러 규칙등을 제시할 수 있다. * (asterisk), ?(question mark), \(back slash)

example)
```bash
// 현재 경로의 test로 시작하는 파일명을 가진 모든파일을 ./subdir 디렉토리로 복사
$cp test* ./subdir

// 현재 경로의 test + 한글자 파일명을 가지는 모든파일을 ./subdir 디렉토리로 복사
$cp test? ./subdir

// 현재 경로의 test 2019 (공백 있음) 파일명을 가지는 파일을 ./subdir 디렉토리로 복사
$cp test\ 2019 ./subdir
```
***

관련링크 

[A CommandLine Premier for Beginner](https://lifehacker.com/a-command-line-primer-for-beginners-5633909)


