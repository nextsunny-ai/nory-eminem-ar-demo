# NORY × EMINEM — AR Alpha Demo

**Live**: https://nextsunny-ai.github.io/nory-eminem-ar-demo/

NORY CITY 페스티벌 헤드라이너 캐스팅(에미넴)을 위한 AR 어필 알파 데모.

## 두 모드

### 1. ENTER THE CITY (Track B — Booth AR · Stage 1)
후면 카메라 + 8 MILE ROAD 표지판 → 탭하면 디트로이트 골목으로 포털 열림.

### 2. BECOME EMINEM (Track B — Hero Hook · Stage 5)
전면 카메라 + MediaPipe 페이스 트래킹 + 얼굴 위에 **블론드 buzz cut** 자동 합성.
- 친구 5명이 한 화면에 들어가면 **전부 다 에미넴** (멀티 페이스)
- 모드: EMINEM / SLIM SHADY / MARSHALL / OFF
- 스크린샷 + 다운로드 + NORY CITY 워터마크 자동

## 브라우저 호환성

| 기기 | 브라우저 | 상태 | 주의 |
|---|---|---|---|
| **iPhone** | **Safari** (iOS 15+) | ✅ 작동 | 권한 거부 시: 설정 → Safari → 카메라 → 허용 |
| **Android** | **Chrome** (80+) | ✅ 작동 | 권한 거부 시: 주소창 🔒 → 권한 → 카메라 |
| **Mac** | Chrome / Safari | ✅ 작동 | 맥미니는 카메라 없음, 별도 USB 카메라 필요 |
| **Windows** | Chrome / Edge | ✅ 작동 | - |

**HTTPS 필수** (GitHub Pages는 자동 HTTPS). `http://` 또는 `file://` 에서는 카메라 권한 거부됨.

## 권한 허용 방법

### iPhone Safari
1. 설정 → Safari → 카메라 → **허용**
2. 사파리 탭 모두 닫기
3. URL 다시 열기 → 팝업에서 "허용"

**또는** 사파리 주소창의 **"AA"** 버튼 → 웹사이트 설정 → 카메라 → 허용

### Android Chrome
1. 주소창 왼쪽 **자물쇠 🔒** 아이콘 탭
2. 권한 → 카메라 → **허용**
3. 페이지 새로고침

**또는** Android 시스템 설정 → 앱 → Chrome → 권한 → 카메라 → 허용

### Desktop Chrome/Safari
주소창 왼쪽 카메라 아이콘 → 허용 → 새로고침

## 공유 방법

### 링크 공유
그냥 URL 한 줄 공유:
```
https://nextsunny-ai.github.io/nory-eminem-ar-demo/
```

### QR 코드 공유
맥에서 QR 생성:
```bash
python3 -c "import qrcode; qrcode.make('https://nextsunny-ai.github.io/nory-eminem-ar-demo/').save('qr.png')"
open qr.png
```

카톡/슬랙/이메일로 QR 이미지 공유. 받는 사람이 폰 카메라로 스캔하면 바로 열림.

## 미팅 시연 팁

에미넴 측(Aftermath / Shady / Interscope) 또는 프로모터 미팅에서:

1. 노트북 또는 아이패드 카메라 켜고 이 URL 열기
2. **BECOME EMINEM** 탭
3. 카메라를 상대방에게 돌리며: "*This is you — as Eminem.*"
4. 옆 사람도 한 프레임에 들어오게 → **두 명이 동시에 에미넴**이 된다
5. 셔터 → 다운로드 → 슬랙/이메일로 미팅 직후 전송

## 프로덕션 업그레이드 계획

이 알파는 "얼굴 각도·크기에 맞춰 2D 헤어를 실시간 합성" 수준. 프로덕션 빌드에서는:

- **3D 헤어 메시** (Blender 모델링 + 헤어 카드) — 실제 조명 반응
- **Slim Shady 만화 셰이더** (셀 쉐이딩 + 외곽선)
- **얼굴 조명 보정** — 현장 조명에 맞춘 컬러 매칭
- **페이셜 블렌드쉐이프** — 표정에 따라 헤어도 미세 반응
- **변신 이펙트** — 모드 전환 시 파티클/프리즘
- **Stage 1~4 연결** — 포털/워크스루/그래피티/셀카 → 이 데모의 CITY 모드를 5단계 풀 여정으로 확장
- **8th Wall / MindAR Image Target** — 실제 8 Mile 표지판 실물 마커 인식

예상 프로덕션 기간: **2~3개월**

## 수정 & 배포

```bash
# 로컬 repo (맥미니)
cd /tmp/nory_demo_repo
# index.html 수정 후
git add index.html
git commit -m "..."
git push
# 1~2분 후 GitHub Pages 자동 반영
```

## 기술 스택 (알파)

- **페이스 트래킹**: MediaPipe Face Landmarker (@0.10.14, GPU delegate, 최대 5명)
- **렌더**: Canvas 2D + 아핀 변환
- **카메라**: `navigator.mediaDevices.getUserMedia`
- **포털/배경**: CSS 애니메이션 + base64 인라인 이미지
- **호스팅**: GitHub Pages (자동 HTTPS)
- **외부 의존성**: jsdelivr CDN (MediaPipe WASM + 모델), 그 외 없음

단일 HTML 파일 1개. 이미지 3장(P4 Bridge, P6 Alley, P7 Graffiti) base64 인라인. 총 ~460KB.

## 라이선스

Confidential — Birch Sound × NORY CITY × Sunny Entertainment.
에미넴 측 어프로치 및 관련 미팅 시연 목적으로만 사용.
