# 🥢 진짜 한국어 (Real Korean Expressions)

사전에 안 나오는 진짜 실생활 한국어 표현을 배우는 플래시카드 웹앱입니다. 막대기(Makdaegi) 한국어 콘텐츠 채널의 복습용 도구로 만들었습니다.

**🔗 [바로 열어보기](https://your-username.github.io/real-korean-expressions/)** (배포 후 실제 링크로 교체)

## 주요 기능

- 🗂️ **플래시카드**: 표현을 보고 뜻을 맞춰본 뒤, 탭해서 뒤집으면 뜻·예문 확인
- 🏷️ **카테고리 필터**: 신조어, 리액션, 줄임말, 일상 관용구로 구분
- 🔊 **발음 듣기**: 실제 목소리(ElevenLabs로 생성) 우선 재생, 없으면 브라우저 내장 음성으로 자동 대체
- ⭐ **학습 진행 추적**: "알아요/아직 헷갈려요"로 표시한 내용이 폰에 저장되어 유지됨
- 🔀 섞기 기능으로 매번 다른 순서로 복습

## 기술 스택

- 순수 HTML/CSS/JavaScript (프레임워크 없음, 단일 파일)
- 발음: [ElevenLabs](https://elevenlabs.io) Text-to-Speech API로 생성한 mp3 + [Web Speech API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Speech_API)(브라우저 내장 음성) 폴백
- GitHub Pages로 무료 정적 호스팅

## 오디오 파일 구조

```
audio/
  01.mp3   ← 1번 표현("킹받다")의 발음
  02.mp3   ← 2번 표현("찐이다")의 발음
  ...
  60.mp3
```

`audio/{번호}.mp3` 파일이 있으면 그걸 재생하고, 없으면 자동으로 브라우저 음성으로 대체됩니다. **60개를 한 번에 다 준비하지 않아도 앱이 정상 작동**하도록 의도적으로 설계했습니다 — 콘텐츠(막대기 영상)가 늘어날 때마다 표현과 음성을 하나씩 추가하는 방식을 염두에 두었습니다.

## 데이터 추가/수정하기

`index.html` 안의 `EXPRESSIONS` 배열에 아래 형식으로 항목을 추가하면 됩니다.

```js
{
  "id": 61,
  "kr": "표현",
  "romanization": "pyohyeon",
  "meaningKo": "뜻 설명",
  "meaningEn": "English meaning",
  "exampleKr": "예문",
  "exampleEn": "Example sentence",
  "category": "slang"  // slang | reaction | abbr | idiom
}
```

새 항목의 발음 mp3도 만들고 싶다면, `make_audio.py` 스크립트에 표현을 추가하고 실행하면 됩니다(스크립트는 API 키가 포함되어 있어 저장소에는 올리지 않았습니다).

## 알고 있는 한계

- 예문(문장)에는 아직 실제 목소리 mp3가 없고, 브라우저 음성으로만 재생됩니다.
- 발음 mp3가 없는 표현은 브라우저/OS의 한국어 음성팩에 따라 발음 품질이 다를 수 있습니다.
