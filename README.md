# SW-Open-Source
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
