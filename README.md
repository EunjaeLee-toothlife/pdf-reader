# 📖 PDF 리더

PDF를 보고, 현재 페이지 텍스트를 음성으로 읽어주는 정적 웹 페이지.

## 스택
- **pdf.js** (CDN, ESM) — 페이지 렌더 + 텍스트 추출(`getTextContent`)
- **Web Speech API** (`SpeechSynthesis`) — 추출 텍스트 음성 합성
- 빌드 도구 없음. `index.html` 하나로 동작.

## 로컬 실행
`file://`로 열면 ES module / worker가 막힐 수 있음. 로컬 서버로 띄울 것:

```bash
python3 -m http.server 8000
# http://localhost:8000 접속
```

## GitHub Pages 배포
1. 새 repo 만들고 push:
   ```bash
   git remote add origin https://github.com/<user>/<repo>.git
   git push -u origin main
   ```
2. repo → **Settings → Pages → Source: `main` 브랜치 / `/root`** 선택.
3. 몇 분 뒤 `https://<user>.github.io/<repo>/` 에서 접속.

## 사용
- **PDF 열기**로 파일 선택 → 캔버스에 렌더.
- **◀ / ▶** 또는 좌우 화살표 키로 페이지 이동.
- **🔊 읽기**로 현재 페이지 음성 재생, **⏹ 정지**로 중단.
- 속도 슬라이더 / 음성 선택(한국어 우선 정렬) 지원.

## 한계
- 음성 품질·한국어 voice 유무는 OS/브라우저 의존 (Chrome+macOS 권장).
- 스캔 이미지 PDF는 텍스트가 없어 읽기 불가 (OCR 미포함).
- 파일은 브라우저 내에서만 처리, 서버 업로드 없음.
