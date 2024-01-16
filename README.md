# kiwowki.github.io

## GIT 블로그 만들기

강서현의 깃허브 블로그입니다.

1.  github에 repository 생성(이름: kiwowki(깃허브 이름).github.io)

2.  README.md와 index.html 추가

3.  ruby, Jekyll 다운로드
    Ruby는 동적이고 객체지향적인 프로그래밍 언어입니다. 처음에는 웹 개발에 주로 사용되었지만, 다양한 분야에서 사용되고 있어요. Rails 프레임워크로 유명한데, 이는 웹 응용프로그램을 빠르게 개발할 수 있게 도와줘요. Ruby는 간결하고 가독성이 높은 문법을 가지고 있어 새로운 프로그래머들이 배우기에도 좋은 언어입니다.

    1. [루비 다운로드 홈페이지](https://rubyinstaller.org/downloads/)
    2. Jekyll 다운 받기(`gem install bundler `, `gem install jekyll`)

4.  index.html 삭제 후 `jekyll new ./ ` 하기

5.  테마 골라서 적용하기! [참고](https://zeddios.tistory.com/1223)
    1.  [jekyll 테마 사이트](https://jamstackthemes.dev/ssg/jekyll/)
    2.  깃허브 들어가서 폴더 전체 다운로드
    3.  복사 붙여넣기 하기(겹치는 부분 덮어쓰기)
    4.  `bundle install` 입력
    5.  `bundle exec jekyll serve` 입력
    6.  Server address: `http://127.0.0.1:4000` 로 들어가서 확인하기
    7.  \_config.yml에서 css 등 디테일 수정(`bundle exec jekyll serve` 로 로컬 업데이트 하고 보면서 수정하기)
    8.  git에 push한 후 `kiwowki.github.io` 에 접속하여 확인.

## 블로그 글 쓰기

1.  글 쓰기: \_posts 폴더에서 글 쓰기
    1. 제목 한글 가능, 카테고리 아무거나 설정 가능
    2. 제목은 규칙에 맞게 작성해야 뜸(0000-00-00-abc.md)
2.  이미지 삽입
    1. \_config.yml에 url: https://kiwowki.github.io 추가.
    2. images폴더 안에 해당 post제목을 폴더로 만들고 그 안에 이미지 파일 추가.
    3. `![kiwowki]({{site.url}}/images/2024-01-16-first_posting/blue-4.gif)` 로 이미지 추가하기 (중괄호 2개는 Jekyll에서 사용되는 Liquid 태그의 일부입니다. Liquid은 템플릿 언어로서, Jekyll에서는 정적 사이트를 빌드할 때 변수, 제어 구조, 필터 등을 사용하는 데에 활용됩니다.)
    4. 이미지 + 캡션 중앙정렬(테이블 사용하기)
    ```md
    ![kiwowki]({{site.url}}/images/2024-01-16-first_posting/blue-4.gif) {:class="img-responsive"}
    *대신 이쁜 꽃을 드리겠습니다.*
    -> p > img, em: 좌측정렬 이미지 + 캡션

    | ![kiwowki]({{site.url}}/images/2024-01-16-first_posting/blue-4.gif) | 
    -> table > tbody > tr > td : 중앙정렬 이미지

    | ![kiwowki]({{site.url}}/images/2024-01-16-first_posting/blue-4.gif) | 
    |:--:| 
    | 여기에 캡션을 작성합니다. |
    -> table > thead > tr > th / table > tbody > tr > td : 중앙정렬 이미지 + 캡션
    ```
    ```scss
    table {
        width: 100%;
        th,
        td {
            padding: 8px 13px;
            // border: 1px solid #dfe2e5;
            
        }
        th {
            // background-color: #eee;
            font-family: Raleway;
        }
    }
    ```
3. 댓글 기능(disqus 사용)
    1. _config.yml 파일의 `plainwhite:`의 하위 속성으로 `disqus_shortname: KSH_blog` 작성.
    이름은 무엇이든 상관없지만 Disqus에서 사용자의 웹사이트를 식별하는 데 사용되는 고유한 식별자이니 고려해서 작성.
- 주의할 점: 글을 수정하면 댓글이 다 날아감으로 주의해서 수정할 것.    

## 트러블 슈팅

<details>
<summary> jekyll new ./ 시 exists and is not empty 가 뜨는 에러</summary>

`jekyll new ./`를 하면

```bash
Conflict: C:/Users/line/Documents/github/kiwowki.github.io exists and is not empty.
Ensure C:/Users/line/Documents/github/kiwowki.github.io is eor else try again with `--force` to proceed and overwritefiles.
```

가 떴다.
index.html을 삭제하고 dir을 통해 확인한 결과 git폴더와 README.md를 빼고는 아무런 파일이 없음에도 비어있지않다는 오류가 떠서 README.md도 삭제한 후 jekyll new ./ 를 실행해서 해결.
참고한 사이트에서는 index.html만 삭제하라고 했는데 이유는 모르겠음.

</details>

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
