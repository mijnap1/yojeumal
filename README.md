<p align="center">
  <img src="./yojeumal-icon.png" width="112" alt="요즘말 로고">
</p>

<h1 align="center">요즘말</h1>

<p align="center">
  그때 우리는 이렇게 말했다.
</p>

<p align="center">
  <a href="./">Timeline</a> ·
  <a href="./about/">About</a> ·
  <a href="./sources/">Sources</a>
</p>

<br>

## 2020—NOW

요즘말은 유행어를 시간 위에 올려둔 작은 아카이브입니다.

어떤 말은 너무 빨리 지나가서, 분명 다 같이 썼는데도 나중에 보면 어디서 시작됐는지 잘 기억나지 않습니다. 이 사이트는 그런 말들을 날짜와 함께 모아둡니다. 단어를 누르면 뜻, 유래, 예시를 볼 수 있고, 몇몇 항목은 카드를 뒤집어 당시 장면도 함께 볼 수 있습니다.

<br>

## Features

**Horizontal timeline**

2020년부터 현재까지의 유행어를 하나의 긴 시간축 위에 배치합니다. 마우스 드래그, 트랙패드, 휠, 모바일 스와이프를 모두 지원합니다.

**Context cards**

단어를 누르면 뜻, 유래, 사용 상황, 예문이 한 카드 안에서 열립니다. 단어만 저장하는 게 아니라 그 말이 쓰인 분위기까지 같이 보여주는 구조입니다.

**Archive frames**

일부 유행어에는 원본 장면을 가공한 이미지가 들어갑니다. 카드 오른쪽 화살표를 누르면 앞면의 설명에서 뒷면의 이미지로 전환됩니다.

**Permalinks**

각 유행어는 고유한 URL 해시를 가집니다. 예를 들어 특정 단어를 연 상태에서 링크를 공유하면, 다시 들어왔을 때 같은 카드가 바로 열립니다.

**Responsive layout**

큰 화면에서는 넓게 훑고, 모바일에서는 카드와 화살표 위치가 흐트러지지 않도록 따로 조정했습니다.

<br>

## Code

The site is intentionally small: plain HTML, CSS, and JavaScript. No build step, no framework, no package install.

```txt
.
├── index.html          # timeline page
├── script.js           # data, layout, drag, cards, permalinks
├── styles.css          # responsive layout and interactions
├── about/index.html    # about page
├── sources/index.html  # source list
└── assets/             # archive frame images
```

The timeline data lives in `script.js` as structured arrays and objects:

```js
const trends = [
  ["2020-01-13", "아무노래 챌린지"],
  ["2021-02-20", "무야호"],
  ["2024-05-08", "완전 럭키비키잖아"],
];

const definitions = {
  "무야호": "아주 신나거나 만족스러운 순간에 외치는 감탄사로 쓰여요.",
};
```

Each term is rendered onto the timeline based on its date:

```js
function xFor(date) {
  return ((new Date(`${date}T00:00:00`) - start) / day) * pixelsPerDay;
}
```

Permalinks are generated from the term itself, so a selected card can be shared directly:

```js
function termToSlug(term) {
  return term
    .normalize("NFC")
    .toLocaleLowerCase("ko-KR")
    .replace(/[^\p{Letter}\p{Number}]+/gu, "-")
    .replace(/^-+|-+$/g, "");
}
```

<br>

## Curation

새로 생긴 줄임말을 전부 넣지는 않습니다.

실제로 사람들이 많이 말했고, 댓글이나 영상에서 반복됐고, 시간이 지나도 “아 그때 그거” 하고 떠오르는 표현을 고릅니다. 정확한 최초 작성자를 찾기 어려운 말은 무리해서 단정하지 않고, 널리 퍼진 시점과 확인 가능한 맥락을 기준으로 정리합니다.

<br>

## Note

날짜는 원본 콘텐츠가 공개된 시점, 또는 유행이 널리 확인된 시점을 기준으로 잡았습니다. 인용된 유행어와 원본 콘텐츠의 권리는 각 권리자에게 있습니다.

<br>

<p align="center">
  <sub>YOJEUMAL — KOREAN SLANG TIMELINE</sub>
</p>
