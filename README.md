# Super Mario - 8 World Adventure (PWA)

갤럭시 안드로이드 및 모든 모던 브라우저에서 작동하는 Progressive Web App 슈퍼마리오 게임.

## 📦 파일 구조
```
super-mario-pwa/
├── index.html           # 게임 메인 파일
├── manifest.json        # PWA 메니페스트
├── service-worker.js    # 오프라인 캐싱
├── .htaccess            # Apache 서버용 MIME 설정
└── icons/
    ├── icon-192.png
    ├── icon-512.png
    ├── icon-maskable-512.png
    └── screenshot-1.png
```

## 🚀 서버 배포 방법

### 옵션 1: 정적 호스팅 (추천)
Netlify, Vercel, GitHub Pages, Firebase Hosting 등에 `super-mario-pwa` 폴더의 내용물을 그대로 업로드하면 됩니다.

### 옵션 2: 전통적 웹서버 (Apache / Nginx / Cafe24 / Gabia)
1. FTP로 웹루트(`public_html` 등)에 `super-mario-pwa` 폴더 전체 업로드
2. **반드시 HTTPS로 접속** (서비스워커는 HTTPS에서만 작동, `localhost`는 예외)
3. 브라우저에서 `https://your-domain.com/super-mario-pwa/` 접속

### Nginx 설정 예시
```nginx
location /super-mario-pwa/ {
    add_header Service-Worker-Allowed "/";
    types {
        application/manifest+json  webmanifest;
    }
}
```

## 📱 갤럭시(Android)에서 앱으로 설치하기

1. Chrome 또는 삼성 인터넷 브라우저로 게임 URL 접속
2. 하단에 나타나는 **"📥 앱 설치하기"** 버튼 클릭
3. 또는 Chrome 메뉴(⋮) → **"홈 화면에 추가"** 선택
4. 홈화면의 슈퍼마리오 아이콘 탭 → 풀스크린 게임 시작!

## 🎮 조작법
- **가로 모드** 권장 (세로모드에서는 회전 안내 표시)
- D-Pad 좌측: ◀ ▶ 이동
- 우측 버튼: JUMP (초록) / RUN (주황, 파이어플라워 획득 시 파이어볼 발사)

## 🗺 8개 월드
1. World 1-1 오버월드 | 2. World 1-2 동굴 | 3. World 2-1 평원 | 4. World 2-2 하늘
5. World 3-1 야간 | 6. World 3-2 성채 | 7. World 4-1 갠틀릿 | 8. World 4-2 쿠파 성 (보스전)

## ⚙️ 기술 스택
- Vanilla JavaScript + HTML5 Canvas (외부 라이브러리 無)
- Service Worker로 오프라인 플레이 지원
- Web App Manifest로 네이티브 앱 설치
- Touch Events + Keyboard 입력 겸용

## 🔒 HTTPS 필수
Service Worker와 "홈 화면에 추가" 기능은 HTTPS에서만 작동합니다.
Let's Encrypt로 무료 SSL을 적용하거나 Netlify/Vercel 등 HTTPS 기본 제공 서비스를 사용하세요.

## 테스트 (로컬)
```bash
# Python 간이 서버
cd super-mario-pwa
python3 -m http.server 8000
# http://localhost:8000 접속
```
