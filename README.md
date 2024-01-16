## GIT 블로그 만들기



## 트러블 슈팅
<details>
<summary>Whitespace 에러</summary>
유닉스 시스템에서는 한 줄의 끝이 LF(Line Feed)로 이루어지는 반면,
윈도우에서는 줄 하나가 CR(Carriage Return)과 LF, 즉 CRLF로 이루어지는데
Git이 이 둘 중 어느 쪽으로 선택할지 혼란이 온 것이다.

해결방법

`git config --global core.autocrlf true` // 시스템 전체에 적용
⠀
`git config core.autocrlf true` // 해당 프로젝트에만 적용

</details>
````