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

Yojeumal is a small timeline archive for Korean slang and internet language.

Some phrases move fast. Everyone uses them for a while, then a few months later it is hard to remember where they came from or why they were funny. This site keeps those words on a timeline, with short notes on meaning, origin, and use. Some cards also include an archive frame from the moment the phrase came from.

<br>

## Features

| Feature | Detail |
| --- | --- |
| Timeline | Places Korean slang from 2020 to now along one horizontal timeline. |
| Drag | Supports mouse drag, trackpads, wheel scrolling, and mobile swipe. |
| Cards | Opens meaning, origin, usage context, and examples in one focused card. |
| Frames | Lets selected cards flip to an image from the original meme or source moment. |
| Links | Updates the URL for each open card, so individual terms can be shared directly. |
| Mobile | Adjusts card width, spacing, and flip controls for smaller screens. |

<br>

## Code

The project runs as static files. There is no build step and no framework.

```txt
.
├── index.html
├── script.js
├── styles.css
├── about/
├── sources/
└── assets/
```

The slang data lives in `script.js`. Dates, definitions, origins, examples, and media are kept in separate objects, linked by the same Korean term key.

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

Dates are converted into pixel positions on the timeline.

```js
function xFor(date) {
  return ((new Date(`${date}T00:00:00`) - start) / day) * pixelsPerDay;
}
```

When a card opens, the term becomes the URL hash. Korean text is normalized first, then converted into a shareable slug.

```js
function termToSlug(term) {
  return term
    .normalize("NFC")
    .toLocaleLowerCase("ko-KR")
    .replace(/[^\p{Letter}\p{Number}]+/gu, "-")
    .replace(/^-+|-+$/g, "");
}
```

Only cards with archive images need an entry in `mediaDetails`.

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

Not every new abbreviation belongs here.

The archive focuses on phrases that people actually repeated in conversation, comments, videos, and edits. If the exact first use is unclear, the timeline uses the point where the phrase became widely recognizable instead of pretending there is a perfect origin date.

<br>

## Note

Dates are based on either the original release date or the period when the phrase became widely visible. Quoted phrases and source media belong to their respective rights holders.

<br>

<p align="center">
  <sub>YOJEUMAL — KOREAN SLANG TIMELINE</sub>
</p>
