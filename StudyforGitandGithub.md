# Git이란?

소스코드를 효과적으로 관리하기 위해 개발된 '분산형 버전 관리 시스템' 입니다. 원래는 Linux 소스코드를 관리할 목적으로 개발 되었습니다.


Git에서는 소스코드가 변경된 이력을 쉽게 확인할 수 있고, 특정 시점에 저장된 버전과 비교하거나 특정 시점으로 되돌아갈 수도 있습니다.


또 내가 올리려는 파일이 누군가 편집한 내용과 충돌한다면, 서버에 업로드 할 때 경고 메세지가 발생됩니다. 그러므로 누군가 편집한 내용을 덮어써버리는 실수를 예방할 수 있습니다.


# Git의 기본



### 이력을 관리하는 저장소 ###


저장소(Git repository)란 말그대로 파일이나 폴더를 저장해 두는 곳입니다. 그런데 Git 저장소가 제공하는 좋은 점 중 하나는 파일이 변경 이력 별로 구분되어 저장된다는 점입니다. 비슷한 파일이라도 실제 내용 일부 문구가 서로 다르면 다픈 파일로 인식하기 때문에 파일을 변경 사항 별로 구분해 저장할 수 있습니다.



### 원격 저장소와 로컬 저장소 ###


Git은 원격 저장소와 로컬 저장소 두 종류의 저장소를 제공합니다.

- 원격 저장소(Remote Repository): 파일이 원격 저장소 전용 서버에서 관리되며 여러 사람이 함께 공유하기 위한 저장소입니다.
- 로컬 저장소(Local Repository): 내 PC에 파일이 저장되는 개인 전용 저장소입니다.


평소에는 내 PC의 로컬 저장소에서 작업하다가 작업한 내용을 공개하고 싶을 때에 원격 저장소에 업로드 합니다. 물론 원격 저장소에서 다른 사람이 작업한 파일을 로컬 저장소로 가져올 수도 있습니다.



### 저장소 만들기 ###

내 PC에 로컬 저장소를 만드는 방법은 2가지 입니다.

- 아예 저장소를 새로 만드는 방법
- 이미 만들어져 있는 원격 저장소를 로컬 저장소로 복사해 오는 방법



### 변경을 기록하는 커밋 ###

파일 및 폴더의 추가/변경 사항을 저장소에 기록하려면 <u>커밋(commit)</u> 을 해줘야 합니다.

커밋을 실행하면 이전 커밋 상태부터 현재 상태까지의 변경 이력이 기록된 커밋(리버전)이 만들어 집니다.

최근 커밋부터 거슬러 올라가면 과거 변경 이력과 내용을 알수 있습니다.

각 커밋에는 영문/숫자로 이루어진 40자리 고유 이름이 붙습니다. 저장소에선 이 40자리 이름을 보고 각 커밋을 구분하고 선택합니다.


커밋은 이렇게 이력을 남기는 중요한 작업이기 때문에 커밋을 실행할때 **커밋 메세지**를 필수로 입력해야 합니다. 메세지가 없으면 커밋이 실행되지 않습니다. **커밋 메세지**는 아래참고
```swift
1번째 줄 : 커밋 내의 변경 내용을 요약

2번째 줄 : 빈 칸

3번째 줄 : 변경한 상세 이유
```


### 작업트리(Work tree)와 인덱스(Index)

Git 에서는 우리가 흔히 말하는 폴더(디렉토리)를 '작업트리'(Work tree)라고 부릅니다. 그리고 커밋을 실행하기 전의 저장소와 작업트리 사이에 존재하는 공간을 '인덱스'(Index)라고 합니다.

*참고. 인덱스에 등록되지 않은 파일은 커밋이 되지 않습니다.*

Git의 '커밋' 실행은 '작업트리'에 있는 변경 내용을 저장소에 바로 기록하는 것이 아니라 그 사이 공간인 '인덱스'에 파일 상태를 기록(stage - 스테이징 한다고 표현하기도 함)하게 되어 있습니다. 따라서 저장소에 변경 사항을 기록하기 위해서는, 기록하고자 하는 모든 변경 사항들이 '인덱스'에 존재해야 합니다.

예를 들어, 10개의 파일을 수정했지만 그 중에 7개만 저장소에 공개하고 싶을 때는 변경한 10개의 파일 중 7개를 선택하는 작업이 바로 '인덱스에 등록' 또는 '스테이징(stage)' 이라 표현하는 작업 입니다.

이렇게 인덱스란 공간(가상공간)이 중간에 있는 덕분에 작업트리 안에 있는 커밋이 필요 없는 파일들을 커밋에 포함하지 않을 수 있고, 파일에서 내가 원하는 일부 변경 사항만 인덱스에 등록해 커밋할 수 있습니다.



# Practice #1 Git의 기본
### Git 설치

Mac의 iTerm이나 Terminal에서 Git을 이용하려면, Git 웹사이트에서 설치 파일을 다운로드하여 설치해야 합니다.  또한 Homebrew를 이용하는 방법도 있습니다. 

Homebrew를 이용하는 것을 추천 합니다. Homebrew 링크 : https://brew.sh/index_ko Git 링크 : http://git-scm.com/ 

설치가 끝나면, Terminal이나 iTerm을 실행 합니다.

확인을 위해 version 명령어를 실행합니다. Git의 버전이 표시되면 설치에 성공한 것입니다. 출력되는 문자열은 설치된 환경과 버전에 따라 다를 수 있습니다.

Git 버전확인 명령어 : *git —version*

![예시화면](https://user-images.githubusercontent.com/47494240/54026271-9e8c8600-41e0-11e9-8cc7-c327626572de.png)



### Git 초기설정

설치한 Git에 본인의 사용자명과 메일 주소를 등록 합니다. 등록한 사용자명과 메일 주소는 나중에 변경이력등에 표시됩니다.

config 명령어를 이용해 설정을 진행하겠습니다.

사용자명 등록 명령어 : *git config —global user.name 본인이름 or 닉네임*

사용자 이메일 등록 명령어 : *git config —global user.email 메일주소*

![예시화면](https://user-images.githubusercontent.com/47494240/54027337-89195b00-41e4-11e9-90c2-43351e71a69e.png)



### 새 저장소 만들기

#### 먼저 로컬에 gitTest라는 이름으로 빈 폴더를 만들어 로컬 저장소로 등록해 보겠습니다. ####

#### 우선 gitTest라는 Desktop에 생성해 줍니다. gitTest 폴더를 Git의 저장소로 등록하려면, 해당 폴더로 이동하여 init 명령어를 사용합니다. ####

따라해보기) iTerm이나 Terminal을 실행한 후 먼저 <kbd>l</kbd><kbd>s</kbd> *ls* 명령어를 입력하여 본인이 어디 위치에 있는지 확인 합니다. ls 명령어를 입력하면 이동할수 있는 폴더명과 파일 이름들이 나옵니다.

그후 *cd Desktop*을 입력하여 Desktop 폴더로 이동합니다.

저는 gitTest 폴더를 이미 생성하였지만 이글을 보시는 분들은 새로 생성하셔야 하니 *mkdir gitTest* 라고 입력하여 gitTest폴더를 생성합니다. 다시 *ls*를 입력하면 gitTest라는 폴더가 보입니다. 그후 다시 *cd gitTest*를 입력하여 폴더로 이동합니다.

이제 저장소 등록 명령어인 *git init*을 입력합니다. 전 이미 해놔서 다른 메세지가 뜨지만 처음 폴더를 저장소로 등록하면 이렇게 출력 됩니다. Initialized empty Git repository in/Users/yourname/Desktop/gitTest/.git/ 이 메세지가 출력되었다면 성공적으로 완료 된 겁니다.

![예시화면](https://user-images.githubusercontent.com/47494240/54070277-48cbe280-42a1-11e9-8591-fd9497095bf6.png)



### 파일 커밋(commit)하기

우선 iTerm이나 Terminal에서 자주 사용하는 명령어를 보시겠습니다.

> ls 목록조회, ls -all 숨김목록까지 조회, cd 경로이동, pwd 경로확인
>
> mkdir 디렉토리생성, rmdir 디렉토리 삭제
>
> touch 파일생성, cp 복사, mv 이동, rm 삭제
>
> vi / vim / nano 등등 해당에디터 실행, cat 파일내용출력, head / tail 파일 상단/하단 내용 출력
>
> man 명령어메뉴얼확인, history 입력한명령어목록출력, ; 다중명령어실행
>
> open 지정한경로를 Finder로 열거나 파일실행
>
> chmod 파일속성변경
>
> clear 화면 클리어, exit 종료

#### gitTest 폴더에 *gitstudy.txt*파일을 추가하고, 원격 저장소에 파일을 등록해보겠습니다.

우선 iTerm이나 Terminal을 실행시킨 후 cd 명령어를 이용하여 gitTest폴더로 이동합니다.

gitTest폴더로 이동 후 *touch gitstudy.txt* 라는 명령어를 입력하여 gitstudy.txt 파일을 생성합니다. 그후 *vim gitstudy.txt* 명령어를 입력하여 vim 에디터로 들어가겠습니다.

![예시화면](https://user-images.githubusercontent.com/47494240/54070638-b712a400-42a5-11e9-8cba-5fc5ca639297.png)

vim 에디터에 들어가면 아래와 같은 화면이 나옵니다. 아무것도 입력할 수 없고, 처음 접하신 분들은 이게 뭐지라고 생각하게 됩니다. 

![화면](https://user-images.githubusercontent.com/47494240/54070643-bc6fee80-42a5-11e9-9a0c-a0527db9c10a.png)

그럼 vim에디터에서 메세지를 입력할 수 있도록 키보드 <kbd>i</kbd> i키를 누릅니다. 그럼 아래 화면과 같이 밑에 insert라는 메세지가 출력되며 이제 메세지를 입력할 수 있게 됩니다.

![화면](https://user-images.githubusercontent.com/47494240/54070644-c1cd3900-42a5-11e9-81dc-df1faae35c0c.png)

이제 여기에 아래화면 처럼 hello, git 이라고 메세지를 입력합니다. 메세지는 아무거나 입력해도 상관 없습니다.

![화면](https://user-images.githubusercontent.com/47494240/54070646-c5f95680-42a5-11e9-95e1-338b9931ef82.png)

메세지를 다 입력한 후 키보드의 <kbd>esc</kbd> esc키를 누룬후 저장후 vim에디터에서 나가기 명령어인 *:wq* 라고 입력 합니다. 아래화면 참조하세요.

![화면](https://user-images.githubusercontent.com/47494240/54070649-ca257400-42a5-11e9-89cf-dd1decdc09e9.png) 

이제 vim에디터에서 빠져나와 아래와 같이 iTerm이나 Terminal 화면이 보일 겁니다. 그럼 메세지가 입력이 잘 되었는지 *cat gitstudy.txt* 라는 명령어를 입력하여 메세지를 확인 합니다. 본인이 입력한 메세지가 출력된다면 성공적으로 마무리 된 것 입니다.

![화면](https://user-images.githubusercontent.com/47494240/54070652-ceea2800-42a5-11e9-9a39-477d778444fa.png)

Git의 관리 하에 있는 폴더의 작업트리와 인덱스 상태를 확인하려면, status 명령어를 사용합니다. 명령어 *git status*를 타이핑 합니다. 아래화면을 보시면 저는 여러 파일이 있어서 여러가지 파일이 뜨지만 따라하시는 분들은 Untracked files: 라는 메세지부터 파일명까지 뜨실 겁니다.

![화면](https://user-images.githubusercontent.com/47494240/54070886-453c5980-42a9-11e9-9630-2713ab0ca13e.png)

이력 추적 대상이 되지 않은 파일(untracked files)로 gitstudy.txt 파일이 보입니다. 처음 한번만 인덱스에 등록하면 추적 대상으로 등록할 수 있습니다.

파일을 인덱스에 등록하는 명령어는 add 입니다. 뒤에 파일명을 붙여 인덱스에 등록할 파일을 지정합니다. 한칸 띄어쓰기해서 여러개 파일을 한번에 지정할수도 있습니다.

인덱스에 등록하는 명령어 *git add gitstudy.txt* 를 입력하고 다시 상태를 확인하는 *git status* 를 입력하면 아래화면처럼 출력 됩니다.

![화면](https://user-images.githubusercontent.com/47494240/54070896-59805680-42a9-11e9-850e-0d0b8ba02775.png)

인덱스에 gitstudy.txt파일이 추가되었으니 커밋 준비는 끝입니다. 이제 commit 명령어를 실행해 커밋을 진행합니다. commit 명령어 포맷은 다음과 같습니다. *git commit -m "댓글"* 

이제 명령어를 입력해 보겠습니다. *git commit -m "first commit"* 을 입력 합니다. 그 후 다시 상태확인을 위해 *git status*를 입력합니다. 아래화면 참조

![화면](https://user-images.githubusercontent.com/47494240/54070903-6604af00-42a9-11e9-985f-13b6dacd5177.png)

이제 모든 변경사항이 커밋되었습니다.

저장소의 변경이력을 확인해 봅시다. 저장소 변경 이력을 보려면 log 명령어를 사용합니다. *git log* 를 입력 하면 아래와 같이 화면이 출력 됩니다. 아래 화면에서 빠져 나오는 명령어는 <kbd>q</kbd> q를 누르시면 됩니다.

![화면](https://user-images.githubusercontent.com/47494240/54070921-72890780-42a9-11e9-9ff9-96a03060a9ea.png)

참고) *gitk 라고 입력하시면 변경이력을 GUI에서 확인할 수 있습니다. git을 설치할 때 gitk라는 툴도 동시에 설치됩니다.



# 저장소 공유

### 원격 저장소에 푸시(Push)하기

위에서 로컬 저장소의 기본적인 사용 방법을 설명하고 실습을 했습니다. 이제부터는 원격 저장소를 이용하여 로컬 저장소의 변경 이력을 공유하는 방법에 대해 알아 보겠습니다.

#### push

내 PC의 로컬 저장소에서 변경된 원격 저장소에 공유하려면, 로컬 저장소의 변경 이력을 원격 저장소에 업로드해야 합니다.

웹 상의 원격 저장소로 변경된 파일을 업로드하는 것을 Git에서는 푸시(push)라고 합니다. push를 실행하면, 원격 저장소에 내 변경 이력이 업로드되어, 원격 저장소와 로컬 저장소가 동일한 상태가 됩니다.

### 원격 저장소 복제(Clone)하기

누군가의 변경 이력이 적용된 원격 저장소가 있으면, 그걸 웹에서 통째로 복제해서 내 PC에서 직접 작업할 수 있습니다.

#### clone

원격 저장소를 복제하려면, 클론(clone)이라는 조작을 수행합니다.

복제란 원격 저장소의 내용을 통째로 다운로드하는 것을 말합니다. 복제한 저장소를 다른 PC에서 로컬 저장소로 사용할 수 있게 됩니다.

참고) 변경이력도 함께 로컬 저장소에 복제되어 오므로, 원래 원격 저장소와 똑같이 이력을 참조하고 커밋을 진행할 수 있습니다.

### 원격 저장소에서 풀(Pull)해오기

원격 저장소를 공유해 여러 사람이 함께 작업을 하면, 모두가 같은 원격 저장소에 푸시(Push)합니다. 그럼 다른 사람이 원격 저장소에 올려놓은(Push) 변경 내용을 내 로컬 저장소에도 적용(Pull)할 필요가 있습니다.

#### pull

원격 저장소에서 로컬 저장소로 업데이트하려면 풀(pull)을 실행합니다.

pull을 실행하면, 원격 저장소에서 최신 변경 이력을 다운로드하여 내 로컬 저장소에 그 내용을 적용합니다.



# Practice #2 저장소 공유

### Github에 원격 저장소 생성하기

우선은 원격 저장소를 Github상에 만들어 봅니다.

Github 주소: https://github.com/

Github에 접속하여 계정 생성 후 로그인 합니다. 새로운 레파지토리(new repository)를 생성 합니다. 아래 그림 참조

![화면](https://user-images.githubusercontent.com/47494240/54071852-cb5e9d00-42b5-11e9-87ed-6016b7533664.png)

저는 gitTest라는 이름의 새로운 레파지토리를 생성하였습니다. 

![화면](https://user-images.githubusercontent.com/47494240/54071766-c51bf100-42b4-11e9-8533-0fe4491e5e9f.png)

아래 그림처럼 주소부분을 클릭하여 복사합니다. 복사한 Github주소는 remote할때 쓰일 예정입니다.

![화면](https://user-images.githubusercontent.com/47494240/54071767-c9e0a500-42b4-11e9-8769-5ff44568939d.png)



### 원격 저장소에 푸시(Push)하기

#### 원격 저장소에 로컬 저장소의 이력을 Push해보겠습니다.

원격 저장소의 주소는 이름으로 기록해 둘 수 있습니다. 기록 해두면 push 할 때마다 긴 원격 저장소의 주소를 입력 할 필요가 없습니다. 우선 [origin]이라는 이름으로 원격 저장소를 등록하고 push할 예정입니다.

원격 저장소를 추가하려면 remote 명령어를 사용합니다.

remote 명령어: *git remote add 등록명 url*

명령어를 입력해 remote 해보겠습니다. *git remote add origin https://github.com/ChunsuKim/gitTest*

![화면](https://user-images.githubusercontent.com/47494240/54082087-9f91f480-4353-11e9-8558-0eaaaef7e2f9.png)

저장소를 push 하려면, push 명령어를 사용합니다. [repository]는 push 경로의 주소, [refspec]은 push 할 브랜치를 지정합니다. 브랜치에 대한 내용은 나중에 자세하게 설명하겠습니다. 

push 명령어: *git push [repository] [refspec]…*

다음 명령어를 실행해 원격 저장소 origin에 커밋을 push합니다. 실행 옵션에서 한번 *-u* 를 지정하면, 이후에는 브랜치명 지정을 생략할 수 있습니다. 단 비어있는 원격 저장소에 최초로 push했을 때는 원격 저장소명과 브랜치명을 생략할 수 없습니다.

명령어를 입력해 봅니다. *git push origin master* 성공적으로 push가 되었으면 아래 스크린처럼 됩니다.

![화면](https://user-images.githubusercontent.com/47494240/54083700-a2e4aa80-436a-11e9-8b41-ef4f1c91c84d.png)

하지만 아래 스크린처럼 에러 메세지가 뜬다면 다음 스탭을 따라합니다.

![화면](https://user-images.githubusercontent.com/47494240/54083705-b42db700-436a-11e9-9c44-b9616722722a.png)

명령어를 타이핑합니다. *git pull —allow-unrelated-histories origin master* 아래 스크린참조 그후 다시 push를 실행합니다. *git push -u origin master* 그럼 push가 성공했다는 메세지가 나옵니다.

![화면](https://user-images.githubusercontent.com/47494240/54083709-c0b20f80-436a-11e9-872f-fd64f78eb84f.png)

이제 Github에 접속해보면 gitstudy.txt파일이 아래 스크린처럼 push된것을 확인할수 있습니다.

![화면](https://user-images.githubusercontent.com/47494240/54083769-adec0a80-436b-11e9-8379-50f586fd714b.png)



### 원격 저장소 복제(Clone)하기

원격 저장소를 복제하여 다른 곳에서도 작업을 할 수 있도록 만들어 봅시다.

내가 다른 사용자가 됐다고 가정하고 아까 Push했던 원격 저장소의 파일을 내PC로 복사해 오겠습니다.

저장소를 복제하려면 clone 명령어를 이용합니다. 명령어: *git clone 원격저장소URL 폴더명*

명령어를 입력합니다. *git clone https://github.com/ChunsuKim/gitTest gitTest2*

gitTest2라는 새폴더로 Github에 있는 파일들을 복제한다는 뜻입니다. 아래 화면참조

![화면](https://user-images.githubusercontent.com/47494240/54083988-6e72ed80-436e-11e9-805b-ddbe28cb1155.png)

*ls* 를 입력해보면 gitTest2라는 폴더가 생성되었고, *cd gitTest2* 를 입력해 새폴더로 이동해 다시 *ls* 를 입력하면 Github의 파일들이 복제된 것을 확인 할수 있습니다. 위 그림 참조.



### 원격저장소에 다시 푸시(Push)하기

이번에는 로컬 저장소에서 파일을 약간 수정하여 다시 원격 저장소로 파일을 푸시(push) 해보겠습니다.

우선 다시 gitTest폴더내에 있는 gitstudy.txt파일을 vim에디터로 편집해 보겠습니다.

*cd ..* 을 입력하여 gitTest폴더로 이동후 *vim gitstudy.txt* 를 입력하여 vim 에디터로 들어갑니다.

![화면](https://user-images.githubusercontent.com/47494240/54084122-1210cd80-4370-11e9-99be-788a7c48a032.png)

vim 에디터에서 다시 i키를 누른후 아래와 같이 입력합니다. add git test 입력 후 esc키를 누룬후 다시 :wq를 입력하여 빠져나옵니다.

![화면](https://user-images.githubusercontent.com/47494240/54084113-f86f8600-436f-11e9-9f35-b5b059cb5138.png)

이제 다시 add를 실행 후 commit을 하겠습니다. *git add gitstudy.txt* 입력 후 *git commit -m "add 설명을 추가함"* 아래 화면 참조

![화면](https://user-images.githubusercontent.com/47494240/54084125-281e8e00-4370-11e9-80c4-d64998d90e60.png)

그 후 *git push* 를 입력 합니다. 그럼 위 화면처럼 push가 성공한 것을 확인 하실수 있습니다. Github상에 접속하셔서 확인하셔도 바뀐것을 알수 있습니다. 아래 화면참조

![화면](https://user-images.githubusercontent.com/47494240/54084240-a596ce00-4371-11e9-9eaf-18d11ca65804.png)



### 원격 저장소에서 풀(Pull)해오기

원격 저장소에서 gitTest2 폴더로 최신 변경 내용을 가져와 보겠습니다.

먼저 *cd gitTest2* 를 입력하여 gitTest2폴더로 이동합니다. 

![화면](https://user-images.githubusercontent.com/47494240/54084346-d4fa0a80-4372-11e9-87fb-edb1fc564c63.png)

이제 명령어 *git pull origin master* 라고 입력합니다. 그럼 좀아까 변경한 파일들이 gitTest2로 업데이트 됩니다.

![화면](https://user-images.githubusercontent.com/47494240/54084353-e3482680-4372-11e9-858e-a528de7cdfa5.png)

이제 gitstudy.txt 파일이 변경되었는지 확인해 보겠습니다. 명령어 *cat gitstudy.txt* 라고 입력하시면 아래 화면과 같이 출력되면 성공적으로 pull이 되었습니다.

![화면](https://user-images.githubusercontent.com/47494240/54084356-f0fdac00-4372-11e9-810e-f92e3653606f.png)



### Summary

#### Git 명령어

*git config —global user.name 이름* : 이름설정

*git config —global user.email 이메일주소* : 이메일 주소 설정



*git init* : Git 명령어를 사용할 수 있는 디렉토리 지정

*git status* : 현재 상태 확인

*git add 파일명.확장자* : Git 주목 리스트에 파일을 추가

*git add .* : 현재 디렉토리의 모든 파일을 추가

*git commit -m "코멘트"* : 코멘트와 함께 커밋하기

*git commit -a -m "코멘트"* : add 명령을 수행하지 않고 코멘트와 함께 커밋하기(실제로 -a 명령어로 add를 실행함)

*git commit --amend* : 완료한 커밋을 수정     빼먹은 내용을 add후 명령어를 사용

*git diff* : 변경 내용 자세히 살펴보기

*git diff --staged* : 저장소에 커밋한 내용과 staging Area의 내용을 보여줌

*git log* : 히스토리를 조회

*git log -p* : 각 커밋의 diff 결과를 보여줌

*git log -p -2* : 최근 2개의 결과만 보여줌

*git log --stat* : 각 커밋의 통계 정보를 보여줌

*git log --oneline* : 각 커밋을 한줄로 보여줌

*git log --oneline --graph* : 브랜치와 merge 히스토리를 아스키 그래프로 표현해줌



*git remote add origin https://github.com/username/userrepository* : 로컬과 원격 저장소를 연결

*git remote -v* : 연결상태 확인

*git push origin master* : Github로 푸시실행

*git pull origin master* : Github로 풀 실행

*git clone 원격저장소URL 새폴더명* : 원격저장소 Github URL상의 파일을 새폴더로 복제


*git rm 파일명.확장자* : 파일 삭제

*git mv old파일명.확장자 new파일명: old파일명을 new파일명으로 변경
