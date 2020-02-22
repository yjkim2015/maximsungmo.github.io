---
title:  "[Linux] 문자열 검색하기 (grep)"
excerpt: "Linux 내 파일, 폴더 찾기"
toc: true
toc_sticky: true
header:
  teaser: /assets/images/x.jpg

categories:
  - linux
tags:
  - linux
last_modified_at: 2020-02-21T08:00:00-05:00
---

리눅스를 사용하면서 파일을 찾거나 파일 내부의 문자열을 찾는 경우가 많다.

파일 찾는 방법, 파일명으로 찾는 방법, 문자열 찾는 방법에 대해 알아보자.

빠른 사용을 위해서 다음의 코드로 최종 결합된 검색법을 안내함.

## 사용법

### 빠른 참고용 코드(find, grep 혼합)

빠른 사용을 위한 방법을 우선적으로 안내하겠다.

```
find {경로} -name {파일 또는 디렉토리명} | xargs grep --color=auto -n {찾을 문자열}
find /home/cmc -name '*.php' | xargs grep -n 'findme.php'
```

- 해석 : {경로}에서 {파일 또는 디렉토리}에서 찾는다. -> 그 중 {찾을 문자열}이 있는 파일을 찾겠으며 해당 내용의 컬러는 다르게 표시되도록 한다.



### 자주 쓰는 파일 내 문자열 찾기 코드(grep)

```
grep -r {'문자열패턴'} {파일디렉토리}
```

- 해석 : 파일디렉토리의 하위 경로에서 '문자열패턴'에 해당하는 내용을 찾는다.

  

```
grep -i {'문자열패턴'} {파일디렉토리}
```

- 해석 : 문자열 패턴을 대소문자 구분하지 않고 파일디렉토리에서 찾는다. 

  

```
grep -i -r {'문자열패턴'} {파일디렉토리}
```

- 해석 : 문자열 패턴을 대소문자 구분하지 않고 파일디렉토리와 하위디렉토리에서 찾는다.



### 관련 기타 옵션옵션

| 옵션 | 설명                                                 |
| ---- | ---------------------------------------------------- |
| -c   | 검색할 문자열이 속한 행이 개수를 출력한다.           |
| -H   | 파일 이름과 함께 출력을 한다.                        |
| -i   | 대소문을 구분하지 않고 출력을 한다.                  |
| -n   | 찾을려는 문자가 속해있는 행의 번호와 같이 출력 한다. |
| -r   | 현재 경로부터 하위경로까지 검색해서 출력을 한다.     |
| -v   | 찾을려고 하는 문자가 없는 행을 출력 한다.            |
| -w   | 패턴 표현식을 하나의 단어로 취급하여 검색            |



### 파일 찾기 코드 (find)
```
find {경로} -name {파일 또는 디렉토리명}
```

- 해석 : 해당 경로와 하위 경로의 모든 파일을 검색해 조건에 맞는 파일이나 디렉토리를 찾는다. 



```
find {경로} -name {파일 또는 디렉토리명} -type f
```

- 해석 : 파일만 찾는다.



```
find {경로} -name {파일 또는 디렉토리명} -type d
```

-  해석 : 디렉토리만 찾는다.