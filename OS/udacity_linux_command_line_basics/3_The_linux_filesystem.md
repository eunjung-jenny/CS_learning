# 3. The Linux filesystem

## 1) 리눅스 파일시스템 basic

- 디렉토리 & 파일 로 구성
- 작명 규칙
  - `/` 포함 불가
  - 특수 문자(`!` `$` `(` `)` `[` `]` `%` `&` `공백`) 포함시 **quoting**(따옴표로 감싸기) 또는 **escaping**(\로 표현)

- `/var/log/auth.log` : 루트 디렉토리(`/`) - var 디렉토리 - log 디렉토리 - auth.log



## 2) More commands

- `pwd` : present working directory
- `cd [경로]` : change (working) directory
- `mv [이동시킬 파일/디렉토리명] [이동 경로]` : move (rename)
- `cp [이동시킬 파일/디렉토리명]` : copy
- `mkdir [생성할 디렉토리의 절대/상대 경로]`
- `rmdir [삭제할 디렉토리]` : 빈 디렉토리
  - `rmdir -r [삭제할 디렉토리]`

## 3) Globbing

- 파일명을 패턴으로 탐색 (**case sensitive**)

- `ls *html`
- `ls READ*`
- `ls *a*`
- `ls he*lo`
- `ls {css, html}` : css 로 끝나거나 html 로 끝나는 파일
- `ls he?lo` : 임의의 한 글자
- `ls he[aeiou]lo` : 대괄호에 포함된 글자 중 임의의 한 글자



-----

- 추천 수강
  - [Linux for Web Developers](https://www.udacity.com/course/configuring-linux-web-servers--ud299)
  - [How to Use Git and GitHub](https://www.udacity.com/course/how-to-use-git-and-github--ud775)