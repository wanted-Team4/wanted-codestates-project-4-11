# wanted-codestates-project-4-11

사용자가 입력한 설문조가 결과값을 Vue와 chart.js를 이용하여 구현한 프로젝트입니다.

### 📌 &nbsp;[Team4의 과제 확인하러 가기](https://team4-gravylab.netlify.app/)
### <br/>
## 📊 Implement

### Stack
<img src="https://img.shields.io/badge/Vue.js-4FC08D?style=flat-square&logo=Vue.js5&logoColor=white"/> <img src="https://img.shields.io/badge/Chart.js-FF6384?style=flat-square&logo=Chart.js5&logoColor=white"/> <img src="https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=CSS3&logoColor=white"/> <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=JavaScript&logoColor=black"/>

### Features
- [X] 검색 기능 - 기업명 검색을 통해 그래프 확인 가능하며 없는 기업은 별로 안내 메세지 출력된다.
- [X] 펜타곤 그래프 - 펜타곤 그래프로 "적극적인, 자신 있는, 책임 있는, 개인주의, 수평적인" 총 5개의 데이터를 그래프로 확인 가능하다.(미완성)
- [X] 탭 기능 - "모두, 본인, 기업" 총 3개의 기준으로 데이터를 확인이 가능하다.
- [X] 바 그래프 - 바 그래프로 "적극적인, 자신 있는, 책임 있는, 개인주의, 수평적인" 총 5개의 데이터를 그래프로 확인 가능하며 본인만 점수까지 확인 가능하다.

### Contribute

|                        팀원                         |                    맡은역할                     |
| :-------------------------------------------------: | :---------------------------------------------: |
|  <a href="https://github.com/sareum-k">강사름 </a>  |     바 그래프 / 배포    |
| <a href="https://github.com/KooTaehyeon">구태현</a> | 탭 기능 |
|   <a href="https://github.com/sunysty">석지선</a>   |       펜타곤 그래프       |
|   <a href="https://github.com/slobbie">정해석</a>   |       전체 레이아웃 / 상단 바      |
|  <a href="https://github.com/hasunghwa">하성화</a>  |                   검색                   |

### <br/>
## 📊 Directory

```
├── public/
├── src/
│   ├── assets/                  - image files
│   ├── components/              - page components
│   ├── pages/                   - routed pages
│
├── App.vue                      - page routing
├── main.js                      - entry point
├── Data.js                      - data
├── README.md                    - 리드미(프리뷰, 배포링크, 코드컨벤션)
└── package.json                 - 사용 package 목록
```

### <br/>

## 📊 Getting Start

1. `clone` the repository

```
$ git clone "https://github.com/wanted-Team4/wanted-codestates-project-4-11"
```

2. `Install` dependencies

```
$ npm install
```

3. `start` the project

```
$ npm run serve
```

4. `Setting` prettier

```
$ npx prettier --write .
```

## 📊 Commit Emoji

|   emoji    | commit message |       when to use it        |
| :--------: | :------------: | :-------------------------: |
|   :tada:   |     start      |        프로젝트 시작        |
| :sparkles: |      feat      |      새로운 기능 추가       |
|   :bug:    |      fix       |          버그 수정          |
| :recycle:  |    refactor    |        코드 리팩터링        |
| :lipstick: |     style      |   스타일 추가 및 업데이트   |
| :package:  |     chore      |   패키지 추가 및 업데이트   |
|  :books:   |      docs      | 그 외 문서 추가 및 업데이트 |

### <br/>
