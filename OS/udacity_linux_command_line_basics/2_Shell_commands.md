# 2. Shell commands

## 1) more commands

- `man [명령어]` : 명령어 매뉴얼 출력

- 이전에 사용했던 명령어 검색
  - 방향키 ↑, ↓
  - `history`
  - `ctrl + R` : 키워드를 통한 검색
- `unzip [파일명]` : 압축 풀기
- `cat [파일명]` : 파일 내용 출력 (concatenate)
- `wc [파일명]` : 라인수, 단어수, 바이트수 출력
- `diff [파일명]` : 파일들 간의 차이 출력
- `less [파일명]` : 긴 파일 읽을 때 사용
  - [cheatsheet](http://sheet.shiar.nl/less)
  - [regex](https://codular.com/regex)
  - `d` / `u` : page up / page down
  - `<` / `>` : Home / End
  - `[라인#] + enter` : 해당 라인으로 이동
  - `/[검색어] + enter` : 검색어 탐색 ( case sensitive)
    - `n` / `N` : 다음 탐색 결과/ 이전 탐색 결과
- 

## 2) Line-based programs

- `sort` + (정렬을 원하는 데이터 입력) + `ctrl + D`
- `bc` + 계산 + `quit` or `ctrl + D`

## 3) Terminal-based text editor

- `nano [편집할 파일명]`
- `nano` 외에도 `vim`, `emacs`, `joe` 등 존재

