# [과제2] README 파일 작성

## Linux top 명령어
### 1. Linux top 이란?
- 시스템의 상태를 전반적으로 가장 빠르게 파악 할 수 있는 명령어(cpu, memory, process)
- 옵션을 주지않고 입력한다면 interval(3초) 간격으로 화면을 갱신하여 정보를 보여줌.
### 2. top 실행 전 옵션 
- 순간의 정보를 확인하는 `-b` 옵션 (batch 모드)
- 실행 주기를 설정하는 `-n` 옵션 (반복 횟수)
### 3. top 실행 후 명령어
- `shift + p` : cpu 사용률을 내림차순으로 보여줌
- `shift + m` : 메모리 사용률을 내림차순으로 보여줌
- `shift + t`: 프로세스가 돌아가고 있는 시간순으로 보여줌
- `k` : kill.k 입력 후 PID 번호를 작성
- `f` : sort filed 선택 화면이 나옴(q를 누르면 RES순으로 정렬)
- `a` : 메모리 사용량에 따라 정렬함
- `b` : Batch 모드로 작동함
- `1` : CPU Core별로 사용량을 보여줌
### 4.  `top -b -n 1` 예시
![image](https://github.com/iamfreakin/SW-Open-Source/assets/113764802/d6843d96-c6a9-4187-9925-540ef1755656)
- 1 min : 1분 전에 서버가 구동
- load average : 현재 시스템이 얼마나 일을 하는지를 나타soa
  - 3개의 숫자는 1분, 5분, 15분 간의 평균 실행
  - 대기 중인 프로세스의 수. CPU 코어수 보다 적으면 문제 없음
- Tasks : 프로세스 개수
- MiB Mem, Swap : 각 메모리의 사용량
- PR : 실행 우선순위
- VIRT, RES, SHR : 메모리 사용량 => 누수 check 가능
- S : 프로세스 상태(작업중, I/O 대기, 유휴 상태 등)
### 5. VIRT,RES,SHR
- 현재 프로세스가 사용하고 있는 메모리
- VIRT
  - 프로세스가 사용하고 있는 visual memory의 전체 용량
  - 프로세스가 할당된 가상 메모리 전체
  - SWAP + RES
- RES
  - 현재 프로세스가 사용하고 있는 물리 메모리의 양
  - 실제로 메모리에 올려서 사용하고 있는 물리 메모리
  - 실제로 메모리를 쓰고 있는 RES가 핵심
- SHR
  - 다른 프로세스와 공유하고 있는 shred memory의 양

 
## Linux ps 명령어
### 1. Linux ps란?
- 현재 실행중인 프로세스 목록과 상태를 보여줌
- 정확한 옵션 사용이 중요(a와 -a의 옵션이 다른것처럼)
- ps [option]의 사용

### 2. ps 옵션
- `-A` : 모든 프로세스 출력
- `a` : 터미널과 관련된 프로세스를 출력
- `-a`: 세션 리더를 제외하고 데몬 프로세스처럼 터미널에 종속되지 않은 모든 프로세스를 출력
- `-e` : 커널 프로세스를 제외한 모든 프로세스를 출력
- `-f` : 풀 포맷을 보여줌
- `-o` : 출력 포맷을 지정하는 옵션(pid,tty,time,cmd)
- `-m` : 64비트 프로세스를 보여줌
- `-p` : 특정 PID를 지정할때 사용
- `-r` : 실행중인 프로세스를 보여줌
- `-u` :특정 사용자의 프로세스 정보를 확인할 때 사용(사용자를 지정하지 않으면 현재를 기준)
- `-x` : 로그인 상태에 있는 동안 아직 완료되지 않은 프로세스를 보여줌

### 3. ps 명령어 사용 예시
- `ps` 단독 사용
![image](https://github.com/iamfreakin/SW-Open-Source/assets/113764802/7d2aa94b-9e00-4f80-9b91-3d9ffaa6b09b)
  - 기본적으로는 프로세스 번호(PID), 프로세스가 연결된 터미널(TTY),TIME,CMD이 출력
- `ps ax` 사용
![image](https://github.com/iamfreakin/SW-Open-Source/assets/113764802/9df57d5d-c49b-4cef-818f-7a883d8515c3)
  - 시스템에 동작중인 모든 프로세스를 보고싶은 때 사용 (PID,TTY,STAT,TIME,COMMAND 출력)
- `ps aux` 사용
![image](https://github.com/iamfreakin/SW-Open-Source/assets/113764802/4ddf20ca-b1a4-4c58-9887-04682de34dfe)
  - 시스템에 동작중인 모든 프로세스를 소유자 정보와 함께 다양한 정보를 같이 출력(특정 프로세스는 psaux|grep apache)
 
### 4. ps 명령어 사용시 나타낼수 있는 항목
|항목|의미|
|------|-------------------------|
|USER|BSD계열에서 나타나는 항목으로 프로세스 소유자의 이름|
|UID|SYSTEM V계열에서 나타나는 항목으로 프로세스 소유자의 이름|
|PID|프로세스의 식별변호|
|PPID|부모 프로세스 ID|
|%CPU|CPU 사용 비율의 추정치(BSD)|
|%MEM|메모리의 사용 비율의 추정치 (BSD|
|VSZ|K단위 또는 페이지 단위의 가상메모리 사용량|
|RSS|실제 메모리 사용량 (Resident Set Size)|
|TTY|프로세스와 연결된 터미널|
|S, STAT|현재 프로세스의 상태 코드 (S: Sys V, STAT: BSD)|
|TIME|총 CPU 사용 시간|
|COMMAND|프로세스의 실행 명령행|
|STIME|프로세스가 시작된 시간 혹은 날짜|
|C, CP|짧은 기간 동안의 CPU 사용률 (C: Sys V, CP: BSD)|
|F|프로세스의 플래그|
|PRI|실제 실행 우선순위|
|NI|nice 우선순위 번호|

## Linux jobs 명령어
### 1. Linux jobs란?
- 백그라운드에서 실행된 프로그램이나 작업 목록을 보여주는 명렁어
- jobs [옵션] [작업번호] 명령어로 사용
### 2. Linux jobs 옵션
|옵션|설명|
|------|-------------------------|
|-l|프로세스 그룹 ID를 state 필드 앞에 출력|
|-n|프로세스 그룹 중에 대표 프로세스 ID를 출력|
|-p|각 프로세스 ID에 대해 한 행씩 출력|
|command|지정한 명령어를 실행|
  
### 3. Linux jobs 사용 후 상태
|상태|설명|
|------|-------------------------|
|Running|작업이 계속 진행중임|
|Done|작업이 완료되어 0을 반환|
|Done(code)|작업이 종료되었으며 0이 아닌 코드를 반환|
|Stopped|작업이 일시 중단|
|Stopped(SIGTSTP)|SIGTSTP 시그널이 작업을 일시 중단|
|Stopped(SIGSTOP)|SIGSTOP 시그널이 작업을 일시 중단|
|Stopped(SIGTTIN)|SIGTTIN 시그널이 작업을 일시 중단|
|Stopped(SIGTTOU)|SIGTTOU 시그널이 작업을 일시 중단|

## Linux kill 명령어
### 1. Linux kill이란?
- kill 명령어를 통해서 프로세스에 시그널을 보내서 제어하는 명령어
- kill인 이유는 아무런 시그널이 없다면 종료하는 명렁어이기 때문이다
- kill [옵션] [PID]

### 2. Linux kill 옵션
- `-9` : 프로세스 PID를 직접 지정하여 종료
- `-l` : 시그널로 사용할 수 있는 시그널들을 보여줌

### 3. kill 명령어의 시그널 종류
|SIGNAL name|SIGNAL|
|------|-------------------------|
|SIGNIP|HUP|
|SIGHT|INT|
|SIGKILL|KILL|
|SIGSEGV|SEGV|
|SIGTERM|TERM|
|SIGCONT|CONT|
|SIGSTOP|STOP|
|SIGTSTP|TSTP|


---

---
# 마크다운이란

마크다운(MarkDown)은 산문을 읽고, 쓰고, 편집하기 쉬운 목적으로 만들어진 문서 작성을 위한 형식으로 사용되며 문법이 간결하고 HTML삽입이 가능.

## 장점

1. 문법이 간결하고 쉽다.
2. 마크다운은 모든 것에 사용할 수 있음. (웹 사이트, 문서, 메모, 기술 문서 등)
3. 마크다운은 지원하는 플랫폼이 많음. ( Github, Discord 등)
4. 마크다운은 대부분의 환경에서 편집, 작성이 가능. (메모장에서도 가능)
5. 텍스트로 저장되기 때문에 용량이 적어 보관이 용이.

## 단점

1. 모든 HTML의 문법을 대신하지 못함.
2. 표준이 없기 때문에 도구에 따라 변환방식 또는 생성물이 다름.
3. 마크다운으로 파일 업로드하는 경우 저장한 다음 파일 경로를 입력해야되는 불편함
4. tistory, naver blog, notion과는 다르게 문법들을 하나하나 입력해야되는 경우가 있어 귀찮음.

# 사용법

## **제목 (Header)**

- `# + SPACE` 키를 사용하여 생성
- **`<h1>`** 부터 **`<h6>`** 까지 **`#`**을 이용하여 제목을 나타낼 수 있다.
- Notion은 #h3 까지만 지원한다.

```cpp
# h1 제목 1
## h2 제목 2
### h3 제목 3
#### h4 제목 4
##### h5 제목 5
###### h6 제목 6
```
![Untitled](https://github.com/iamfreakin/SW-Open-Source/assets/113764802/05f52fe0-3b09-4b03-801f-289e09162385)

## 줄 바꿈 (Lin**e Breaks)**

- `“  “` 띄어쓰기 두 번 혹은 `<br/>` 로 사용 가능

```cpp
> Line Breaks<br/>Line Breaks
```
![Untitled](https://github.com/iamfreakin/SW-Open-Source/assets/113764802/c4707336-2986-436e-b77f-17d8d68ae97a)


## **수평선 (Horizontal Rule)**

- `---` , `***` , `___` 등 3개 이상 연속된 코드로 사용.

```cpp
---
***
___
```
![Untitled](https://github.com/iamfreakin/SW-Open-Source/assets/113764802/d17ed161-7653-44f0-af78-a7e709f934e2)

## 글자 강조 **(Emphasis)**

- `**굵은 글씨**` : `**` 로 감싸주면 **bold** 효과
- `*기울어짐*`, `_기울어짐_` : `*` , `_` 로 감싸주면 *italic* 효과
- `~~취소선~~` : `~~` 로 감싸주면 ~~strikethough~~ 효과
- `<u>밑줄<u>` : `<u>` 로 감싸주면 underscore 효과

```cpp
**굵은 글씨**  
*이텔릭*  
_이탤릭_  
~~취소선~~  
<u>밑줄</u>  
ex)  
This is the **bold** text and this is the *italic* text and <u>let's</u> do ~~strikethrough~~
```
![Untitled](https://github.com/iamfreakin/SW-Open-Source/assets/113764802/1ae7915c-2b54-405b-b4db-493777111ce8)

## **인용문 (BlockQuote)**

- `>` 블럭 인용 문자를 사용하여 인용문 표현

```cpp
> 인용문장
>> 중첩된 인용문
>>> 중첩된 인용문 2
```
![Untitled](https://github.com/iamfreakin/SW-Open-Source/assets/113764802/63418b46-8425-463a-ba3b-97d6ca36c498)


## **목록 (List)**

- 순서가 필요 없는 목록
- `*`, `+`, `-` 지원
- 문장 맨 앞에 공백 없이 `*` 나 `-` 를 입력하면 순서 없는 목록을 만들 수 있음.

```cpp
- 순서가 필요하지 않은 목록
    - 순서가 필요하지 않은 목록
        - 순서가 필요하지 않은 목록
* 순서가 필요하지 않은 목록
    * 순서가 필요하지 않은 목록
        * 순서가 필요하지 않은 목록
+ 순서가 필요하지 않은 목록
    + 순서가 필요하지 않은 목록
        + 순서가 필요하지 않은 목록

- 순서가 필요하지 않은 목록
    * 순서가 필요하지 않은 목록
    + 순서가 필요하지 않은 목록
```


- 순서가 있는 목록
- 글 앞에 숫자를 입력하면 순서 있는 목록을 만들 수 있음.
- 순서와 상관없이 입력해도 자동으로 숫자가 매겨짐.

```cpp
1. 순서가 필요한 목록
    1. 순서가 필요한 목록
    1. 순서가 필요한 목록
1. 순서가 필요한 목록

1. 순서가 필요한 목록
    9. 순서가 필요한 목록
    3. 순서가 필요한 목록
8. 순서가 필요한 목록
```
![Untitled](https://github.com/iamfreakin/SW-Open-Source/assets/113764802/a0047a2c-016a-4af5-92da-734e2a8c4f5c)

## **표 (Table)**

- `|`(vertical bar) 기호를 통해 테이블을 표현 가능. (가장 좌측, 우측 생략 가능)
- 헤더와 셀을 구분할 때 3개 이상의 -(하이픈, 대시)가 필요.
- `:` (콜론) 기호를 통해 정렬.

```cpp
| Header | value | Description |
| --: | :-- | :--: |
| 정렬 | --: | 우측정렬 |
| 정렬 | :-- | 좌측정렬 |
| 정렬 | :--: | 가운데정렬 |
```
![Untitled](https://github.com/iamfreakin/SW-Open-Source/assets/113764802/9bcd9387-a073-4d60-9a28-c40033033288)



## **코드 (Code)**

- 인라인 코드(Inline Code)
- `백틱 : ``으로 강조할 내용을 감싸면 됨

```cpp
`해당 코드`는 강조할 부분 이다.
```

- 블럭 코드(Block Code)
- ````` c++, html, css, javascript, bash, plaintext 등등

```cpp
#include<iostream>
```
![Untitled](https://github.com/iamfreakin/SW-Open-Source/assets/113764802/93f08b3b-a026-48e3-99c5-dca4518ffbf5)

## **링크 (Links)**

- `[**Title**](**link**)`

```cpp
Click [here](https://www.naver.com/)  
[최범수의Notion](https://www.naver.com/)
```


- 참조 링크 사용법
- `[Title][ID]` 
`[ID]:link "**Optional Title**"`

```cpp
[최범수의Notion][naver]
[naver]: https://www.naver.com/ "누르세요"
```
![Untitled](https://github.com/iamfreakin/SW-Open-Source/assets/113764802/fccf7aa9-1786-4c61-9cfd-4b82c4a51350)

---

## **이미지 (Images)**

- `Link`와 문법이 유사. 앞에 `!`만 추가하면 된다
- `![**대체텍스트**](**이미지주소**)`

```cpp
![최범수](https://mblogthumb-phinf.pstatic.net/20150530_41/owen0418_1432994697524CHNrh_PNG/%BF%F5%C0%CC.PNG?type=w2)
```

- 참조 링크 사용법
- `![**대체텍스트**][**id**]`
`[**id**]: **이미지주소** "**Optional Title**"`

```cpp
![최범수][웅이]

[웅이]:https://mblogthumb-phinf.pstatic.net/20150530_41/owen0418_1432994697524CHNrh_PNG/%BF%F5%C0%CC.PNG?type=w2
```


- 이미지 노출과 동시에 링크 처리
- `[![**대체텍스트**](**이미지주소**)](**링크주소**)`

```cpp
[![최범수]
(https://mblogthumb-phinf.pstatic.net/20150530_41/owen0418_1432994697524CHNrh_PNG/%BF%F5%C0%CC.PNG?type=w2)] 
(https://www.naver.com/)
```
![Untitled](https://github.com/iamfreakin/SW-Open-Source/assets/113764802/7837ccae-d2f0-4518-9bb2-c3e67a179f51)

---

[마크다운 문법정리2_수학수식, 특수문자](https://khw11044.github.io/blog/blog-etc/2020-12-21-markdown-tutorial2/)

---

# Notion 단축키

- `cmd/ctrl + N` : 새 페이지 생성
- `cmd/ctrl + P` : 최근 연 페이지들 띄우기
- `cmd/ctrl + E` : 코드 표시로 변경
- `cmd/ctrl + [ / ]` : 이전, 다음 페이지로 이동
- `cmd/ctrl + shift + L` : 다크모드 전환
- `:[이모티콘 이름]` : 이모티콘 불러오기 *ex) :apple, :사과*
- `cmd/ctrl + I` : 이텔릭체(기울임꼴)로 변경*
- `cmd/ctrl + B` : 볼드체(굵게)로 변경
- `cmd/ctrl + U` : 언더스코어(밑줄)로 변경
- `Tab / shift + Tab` : 들여쓰기, 내어쓰기
- `cmd + ?` : 메뉴바 열기
