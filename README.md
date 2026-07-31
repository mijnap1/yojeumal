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

| Feature | Detail |
| --- | --- |
| Timeline | 2020년부터 현재까지의 유행어를 날짜순으로 배치합니다. |
| Drag | 마우스로 누른 채 끌 수 있고, 트랙패드·휠·모바일 스와이프도 그대로 동작합니다. |
| Cards | 단어를 누르면 뜻, 유래, 쓰는 상황, 예문이 한 번에 열립니다. |
| Frames | 이미지가 있는 항목은 카드를 뒤집어 원본 장면을 볼 수 있습니다. |
| Links | 열린 카드마다 URL이 생겨서 특정 유행어를 바로 공유할 수 있습니다. |
| Mobile | 작은 화면에서는 카드 폭, 여백, 화살표 위치를 따로 조정합니다. |

<br>

## Code

빌드 과정 없이 정적 파일만으로 동작합니다.

```txt
.
├── index.html
├── script.js
├── styles.css
├── about/
├── sources/
└── assets/
```

유행어 데이터는 `script.js` 안에서 관리합니다. 날짜 목록과 카드 내용을 분리해두어, 새 단어를 추가할 때 같은 키만 맞추면 됩니다.

```js
const trends = [
  ["2020-01-13", "아무노래 챌린지"],
  ["2021-02-20", "무야호"],
  ["2024-05-08", "완전 럭키비키잖아"],
];

const definitions = {
  "무야호": "아주 신나거나 만족스러운 순간에 외치는 감탄사로 쓰여요.",
};

const usageDetails = {
  "무야호": ["신나거나 일이 잘 풀렸을 때", "“내일 휴강이다. 무야호!”"],
};
```

날짜는 픽셀 좌표로 변환해서 시간축 위에 놓습니다.

```js
function xFor(date) {
  return ((new Date(`${date}T00:00:00`) - start) / day) * pixelsPerDay;
}
```

카드를 열면 단어 이름으로 URL 해시를 만듭니다. 한국어도 그대로 쓸 수 있게 정규화한 뒤, 공유하기 좋은 형태로 바꿉니다.

```js
function termToSlug(term) {
  return term
    .normalize("NFC")
    .toLocaleLowerCase("ko-KR")
    .replace(/[^\p{Letter}\p{Number}]+/gu, "-")
    .replace(/^-+|-+$/g, "");
}
```

이미지가 있는 카드만 `mediaDetails`에 따로 등록합니다.

```js
const mediaDetails = {
  "무야호": {
    src: "assets/muyaho-archive.webp",
    caption: "Archive frame / 무한도전",
  },
};
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
