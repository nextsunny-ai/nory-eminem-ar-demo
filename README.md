# BECOME EMINEM — Alpha Demo

NORY CITY × EMINEM 부스 AR의 **Stage 5 "Become Eminem"** 헤어 변신 알파 데모입니다. 단일 HTML 파일 한 개로 돌아갑니다.

## 뭐가 되는가

- 🎭 **실시간 페이스 트래킹** (MediaPipe Face Landmarker, GPU)
- 👥 **최대 5명 동시 변신** (멀티 페이스)
- 💇 **블론드 buzz cut + 후드 + 사슬 체인** 실시간 합성
- 🎨 **3가지 모드**: EMINEM / SLIM SHADY (만화 스파이크) / MARSHALL (차분)
- 📸 **스크린샷** + NORY CITY 워터마크 + 해시태그 자동 박힘
- ↻ **전/후면 카메라 전환**
- 📱 **앱 설치 불필요** — 폰 브라우저로 바로 작동

## 어떻게 보여주는가

**옵션 A — 노트북/데스크탑 (미팅에서 시연)**
1. 이 폴더의 `index.html` 을 Chrome / Safari / Edge 로 바로 더블클릭
   (로컬 `file://` 에서는 카메라 권한이 막힐 수 있음 — 아래 옵션 B 권장)

**옵션 B — 간단한 로컬 서버 띄우기 (권장)**

```bash
cd "demo_become_eminem"
python3 -m http.server 8000
```

그리고 브라우저에서 `http://localhost:8000` 접속. 카메라 권한 허용.

**옵션 C — 폰에서 직접 체험 (진짜 느낌)**

1. 맥/PC에서 위 `python3 -m http.server 8000` 을 실행
2. 맥/PC의 로컬 IP 확인 (예: `192.168.0.12`)
3. 폰 브라우저에서 `https://<그 IP>:8000` 접속
   - *주의*: 폰 브라우저는 HTTPS가 아닌 곳에서는 카메라 권한을 보통 거부함
   - 가장 쉬운 방법: ngrok 또는 cloudflared 로 HTTPS 터널 생성
     ```bash
     # ngrok 이 설치되어 있다면
     ngrok http 8000
     # 또는 cloudflared tunnel (설치: brew install cloudflared)
     cloudflared tunnel --url http://localhost:8000
     ```
   - 생성된 `https://xxxxx.ngrok.io` 또는 `https://xxxxx.trycloudflare.com` 주소를 폰 브라우저에 붙여넣기

**옵션 D — 이 파일 그대로 웹 서버에 업로드**

Netlify / Vercel / GitHub Pages / Cloudflare Pages 같은 곳에 `index.html` 한 파일만 드래그-드롭. HTTPS 자동. QR 코드로 폰 공유.

## 써보는 법

1. `START CAMERA` 클릭 → 카메라 권한 허용
2. 얼굴이 화면 안에 들어오면 자동으로 블론드 헤어 + 후드 + 체인이 합성됨
3. 하단 버튼으로 모드 전환: `EMINEM` / `SLIM SHADY` / `MARSHALL` / `OFF`
4. 친구 4~5명이 한 화면에 들어오면 **모두 동시에 변신**
5. 가운데 흰색 큰 버튼 (셔터) → 스크린샷
6. `DOWNLOAD` 로 사진 저장

## 기술 스택 (알파)

- **페이스 트래킹**: MediaPipe Face Landmarker (Google, 무료, CDN)
  - 468 포인트 얼굴 랜드마크 + 멀티 페이스 (최대 5명)
  - GPU 가속
- **렌더**: Canvas 2D + 아핀 변환 (얼굴 회전/크기 추적)
- **카메라**: `navigator.mediaDevices.getUserMedia`
- **워터마크 + 해시태그**: 캔버스 스크린샷 합성 단계에서 박음

## 프로덕션 단계 (이 알파와 차이)

이 알파는 "**얼굴 각도·크기에 맞춰 2D 스티커를 실시간 합성**" 수준입니다. 실제 프로덕션 빌드에서는:

- **3D 헤어 메시** (Blender 모델링 + 헤어 카드) — 실제 조명 반응
- **Slim Shady 만화 셰이더** (셀 쉐이딩 + 외곽선)
- **후드 클로스 시뮬레이션** — 머리 움직임에 따라 자연스럽게 변형
- **얼굴 조명 보정** — 현장 조명에 맞춘 색 보정
- **페이셜 블렌드쉐이프** — 표정에 따라 헤어도 미세 반응
- **모드 전환 애니메이션** — 변신 시 파티클 이펙트
- **Stage 1~4 연결**: 포털/워크스루/그래피티 SLAM 기반 — MindAR Image Target + WebXR

예상 프로덕션 기간: **2~3개월** (Booth AR 전체)

## 미팅 시연 팁

에미넴 측(Aftermath / Shady / Interscope) 또는 프로모터 미팅에서:

1. 노트북을 열고 이 데모를 띄운다 (`http://localhost:8000`)
2. 프론트 카메라로 상대방이 보이게 돌린다
3. "*This is you — as Eminem.*"
4. 옆에 있는 다른 사람도 한 화면에 들어오게 한다 → **두 명 다 동시에 Eminem이 된다**
5. 셔터 → 사진 다운로드 → 슬랙/이메일로 미팅 직후 보내기

알파라도 이것만으로 "**5만 명 관객이 이걸 하게 된다**" 라는 감각을 즉시 전달할 수 있음.

---

*Birch Sound × NORY CITY × Sunny Entertainment*
*Alpha Demo — 2026-04-16*
