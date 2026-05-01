# 선우 ♥ 다인 · 상견례 안내 페이지

## 📁 파일 구성 (배포 전)

배포할 폴더에 아래 두 파일을 함께 두세요.

```
sanggyeonrye/
├── index.html       ← 안내장 본체
├── bgm.mp3          ← 직접 준비하신 배경음악
└── photos/          ← (선택) 캐러셀에 들어갈 사진 6장
    ├── 01.jpg
    ├── 02.jpg
    ├── 03.jpg
    ├── 04.jpg
    ├── 05.jpg
    └── 06.jpg
```

> 음악: `bgm.m4a` 또는 `bgm.ogg`도 자동 인식 (셋 중 하나만 있으면 됨)
>
> 사진: 처음에는 모든 칸이 일러스트 placeholder입니다. 실제 사진으로 바꾸려면
> `index.html`에서 각 placeholder의 `<svg>...<div class="ph-num">XX / 06</div>` 블록을
> `<img src="./photos/01.jpg" alt="" />` 형태로 교체하세요.
> 권장 비율 4:5 (예: 1080×1350px), 각 파일 500KB 이하면 모바일에서 가벼움

---

## 🚀 Vercel 무료 배포 (3가지 방법, 가장 쉬운 순)

### 방법 1. Vercel 웹사이트 드래그 앤 드롭 (가장 쉬움 · 추천)

1. [vercel.com](https://vercel.com) 접속 → GitHub 또는 이메일로 가입(무료)
2. 대시보드 우상단 **Add New… → Project** 클릭
3. **"Deploy without Git"** 또는 **Import Third-Party Git Repository** 옵션 무시
4. 더 간단하게: **[vercel.com/new](https://vercel.com/new)** 페이지에서 폴더 통째로 드래그
5. `index.html`과 `bgm.mp3`가 든 폴더를 그대로 끌어다 놓으면 끝
6. 잠시 후 발급된 URL (예: `your-project.vercel.app`) 을 카톡으로 양가에 공유

### 방법 2. GitHub 연동 (장기적으로 가장 편함)

1. GitHub 저장소를 만들고 두 파일 업로드
2. Vercel에서 해당 레포 Import → 자동 배포
3. 이후 파일 수정 시 GitHub에 푸시만 하면 자동으로 재배포됨

### 방법 3. Vercel CLI

```bash
npm i -g vercel
cd 폴더
vercel --prod
```

---

## ⚙️ Vercel 설정 (옵션)

`package.json`이나 `vercel.json`은 **필요 없습니다**. 정적 HTML 단일 파일 사이트는 Vercel이 자동으로 처리합니다.

다만 음악 파일 캐싱을 위해 `vercel.json`을 추가하면 더 부드럽게 작동합니다 (선택).

```json
{
  "headers": [
    {
      "source": "/bgm.(mp3|m4a|ogg)",
      "headers": [
        { "key": "Cache-Control", "value": "public, max-age=31536000, immutable" }
      ]
    }
  ]
}
```

---

## 📱 호환성 체크리스트

| 환경 | 동작 |
|------|------|
| iPhone Safari | ✅ 음악 토글, 캘린더 추가, 지도 링크 모두 동작 |
| Galaxy Chrome | ✅ 동일 |
| 카카오톡 인앱 브라우저 | ✅ 동작 (캘린더는 외부 브라우저 권장 안내 표시) |
| 데스크탑 | ✅ 480px 중앙 정렬로 모바일 미리보기처럼 표시 |

> ※ 모바일 브라우저는 자동재생을 차단하므로, 우상단 음표 버튼을 한 번 탭하셔야 음악이 시작됩니다. 페이지 로드 후 약 1.5초 뒤 "탭하면 음악이 흘러요" 힌트가 잠깐 노출됩니다.

---

## ✏️ 수정하고 싶을 때

`index.html` 안에서 직접 검색해서 바꾸세요.

| 수정할 내용 | 검색어 |
|-----------|--------|
| 카운트다운 목표 시각 | `2026-05-02T12:00:00+09:00` |
| 식당 정보 | `목 향` 또는 `강매로` |
| 참석자 명단 | `신랑 측` / `신부 측` |
| 초대글 멘트 | `봄 햇살이` |
| 안내사항 4가지 | `단정한 옷차림`, `주차`, `먼저 도착`, `따뜻한 마음` |

---

## 🎵 음악 파일 준비 팁

따뜻한 봄 분위기에 어울리는 무료/저작권 프리 음악은 다음에서 받을 수 있어요:

- **YouTube Audio Library** (가장 추천): https://studio.youtube.com → "오디오 보관함"에서 "Soft / Calm / Cinematic" 필터
- **Pixabay Music**: https://pixabay.com/music/ → "wedding", "spring", "soft piano" 검색
- **Free Music Archive**: https://freemusicarchive.org

권장 사양:
- 길이: 2~4분 (loop 처리되므로 짧아도 무방)
- 음량: 너무 크지 않은 잔잔한 곡 (코드에서 볼륨을 0.4로 자동 조절 중)
- 용량: 3MB 이하 권장 (모바일 데이터 부담 ↓)
