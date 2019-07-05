---
layout: post
title: 리눅스 프로그래밍 With Github - BoB
date: 2019-07-05
excerpt: "리눅스 상에서 프로그래밍을 하고 GitHub를 활용하여 파일관리를 한다."
tags: [git, Linux, Programming, BoB, Best of the Best, Github, Ubuntu, 복습]
comments: true
---

<span style="color:red"> **주의사항** 본 자료는 복습을 위한 Review 자료이며, 문제 시 삭제됩니다.</span>
{: .notice}


## 1. GitHub 회원가입

- Github 링크 <https://www.github.com>
- Gitlab 링크 <https://www.gitlab.com>


## 2. Repository 생성

#### 1. New
<figure>
	<a href="http://www.ddforensic.com/image/repo.png">
  <img src="http://www.ddforensic.com/image/repo.png"></a>
</figure>


#### 2. Repository 이름 지정 
<figure>
          <a href="http://www.ddforensic.com/image/repo1.png">
  <img src="http://www.ddforensic.com/image/repo1.png"></a>
</figure>


## 3. Git 주요 명령어 정리
<pre>
* git config --global user.email "your@email.com"	사용자 이메일 지정
* git config --global user.name "yourname"		사용자 이름 지정
* git config --global --list				설정 확인

* git clone repository_link				clone 가져오기
* git status						작업 상태보기
* git add 파일명						저장소에 파일 추가
* git commit -m "Message"				Message를 지정하고 commit
* git push origin master				로컬저장소의 작업을 Repository로 전송
</pre>

## 4. 사용자의 입력을 받아 팩토리얼 구하는 프로그램 작성

해당 프로그램의 구성요소로는 3가지로 작성한다.

main.cpp / sum.h / sum.cpp

~~~cpp
//main.cpp
#include <cstdio>
#include "sum.h"

int main(){
	int n;
	scanf("%d",&n);

	int s = sum(n);
	printf("sum = %d\n",s);
}

~~~



~~~cpp
//sum.h
#pragma once

int sum(int n);

~~~



~~~cpp
//sum.cpp
#include "sum.h"

int sum(int n){
	return n*(n+1)/2;
}

~~~


위의 3가지 파일들을 g++을 이용하여 빌드한다.


## 5. g++을 이용한 빌드

빌드를 위해서 Makefile을 이용한다.

~~~raw
#Makefile
all: sum

sum: sum.o main.o 
	g++ -o sum sum.o main.o

sum.o: sum.h sum.cpp
	g++ -c -o sum.o sum.cpp

main.o: sum.h main.cpp
	g++ -c -o main.o main.cpp

clean: 
	rm -f sum.o main.o
	rm -f sum

~~~

해당 파일을 작성한 후 make 명령어를 입력하면 sum이라는 실행 파일을 얻을 수 있다.<br>
해당 파일을 실행해보면 사용자의 입력을 받아 해당 숫자의 팩토리얼을 구해주는 프로그램이 실행된다.


