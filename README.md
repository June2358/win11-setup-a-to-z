# 🛠️ Windows 11 Clean Install & Setup Guide (A to Z)

윈도우 포맷 후 초기 세팅을 위한 A to Z 가이드입니다.  
**학교 계정(Education 라이센스)** 활용 및 **개발 환경 호환성**을 고려하여 작성되었습니다.

---

## 📋 1. 포맷 전 준비 (Preparation)

### 1.1. Windows 11 Education 라이센스 확보
학교 계정을 사용하여 무료로 라이센스를 확보합니다.
- [Azure for Students 바로가기](https://azure.microsoft.com/ko-kr/free/students/)

### 1.2. 기존 윈도우 시디키 백업
만약의 사태를 대비해 현재 PC에 입력된 정품 인증 키를 확인하고 백업합니다.
1. `Win` + `X` 키 입력
2. **터미널(관리자)** 또는 **PowerShell(관리자)** 실행
3. 아래 명령어 입력 후 표시되는 키 백업

```cmd
reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SoftwareProtectionPlatform" /v BackupProductKeyDefault
```

### 1.3. Windows 11 디스크 이미지(ISO) 다운로드
- [Microsoft 공식 다운로드 페이지](https://www.microsoft.com/ko-kr/software-download/windows11)

### 1.4. 부팅 USB 제작 (Rufus 활용)

Microsoft 공식 ISO를 Rufus로 USB에 기록합니다.

* [Rufus 다운로드](https://rufus.ie/ko/) / [GitHub](https://github.com/pbatard/rufus)
* Windows 11 ISO 선택 후 `시작`을 누르면 **Windows User Experience** 옵션이 표시됩니다.

#### 권장 설정

* [x] **Remove requirement for 4GB+ RAM, Secure Boot and TPM 2.0**

  * Windows 11 설치 시 RAM, Secure Boot, TPM 2.0 등의 하드웨어 요구사항 검사를 우회합니다.
  * PC가 원래 요구사항을 충족하더라도 설치 USB를 범용적으로 사용할 수 있도록 기본 체크합니다.
  * 이 옵션은 **TPM이나 Secure Boot 자체를 비활성화하는 것이 아니라 설치 프로그램의 요구사항 검사를 제거하는 것**입니다.

* [x] **Remove requirement for an online Microsoft account**
  * Windows 로그인 계정을 Microsoft 계정이 아닌 **로컬 계정**으로 구성할 수 있도록 합니다.
  * 
* [x] **Set regional options to the same values as this user's**
  * 현재 PC의 언어, 키보드, 시간대 등의 지역 설정을 새 Windows에도 적용합니다.

* [x] **Disable data collection (Skip privacy questions)**
  * 설치 중 반복되는 개인정보 관련 질문을 건너뜁니다.

#### 선택 설정
* [ ] **Disable BitLocker automatic device encryption**
  * Windows 설치 후 자동 장치 암호화를 원하지 않는 경우에만 선택합니다.
  * BitLocker/장치 암호화는 분실 시 데이터를 보호하는 보안 기능이므로 필요성을 확인한 뒤 선택합니다.

> **참고:** Rufus 및 Windows 11 버전에 따라 표시되는 옵션 이름이나 설치 과정이 조금씩 달라질 수 있습니다.


### 1.5. 비상용 네트워크 드라이버 (3DP Net)
포맷 직후 인터넷이 잡히지 않는 최악의 상황을 대비합니다.
- [3DP Net 다운로드](https://www.3dpchip.com/3dp/net_down_kor.php)

---

## 🚀 2. 설치 및 초기 설정 (Installation)

### 2.1. 부팅 순서 변경
- BIOS/UEFI 진입 후 부팅 1순위를 **USB**로 설정하여 설치 진행.

### 2.2. 사용자 계정 설정 (⚠️매우 중요)
> **사용자 이름(User Name)은 반드시 '영어'로 설정하세요.** > 한글 이름 사용 시 Python, Anaconda, 일부 개발 툴 경로(Path)에서 인코딩 오류가 발생할 수 있습니다.

### 2.3. 필수 드라이버 및 업데이트
1. **Windows 업데이트**: 설정 -> Windows 업데이트 -> 업데이트 확인 (모두 설치)
2. **장치 관리자 확인**: `Win` + `X` -> 장치 관리자 -> '기타 장치'에 느낌표(!)가 있는지 확인.
3. **Chipset 드라이버**: 사용하는 메인보드/노트북 제조사 홈페이지에서 최신 칩셋 드라이버 설치.

---

## 🧰 3. 필수 유틸리티 (Essential Utilities)

### 3.1. 웹 브라우저
- **[Chrome](https://www.google.com/intl/ko_kr/chrome/)**: 구글 동기화 및 확장 프로그램 활용

### 3.2. 메신저 및 커뮤니케이션
- **[카카오톡 (Microsoft Store 버전)](https://apps.microsoft.com/detail/xp9k178l5g0jq0?launch=true&hl=ko-kr&gl=kr)**

### 3.3. 압축 프로그램 (택 1)
- **[NanaZip](https://github.com/M2Team/NanaZip)**: 윈도우 11 컨텍스트 메뉴(우클릭) 완벽 지원, 오픈소스.
- **[반디집 6.29 (구버전)](https://kr.bandisoft.com/bandizip/old/6/)**: 광고 없는 마지막 무료 버전.
- **[반디집 (최신)](https://kr.bandisoft.com/bandizip/)**: 최신 기능 지원 (무료 버전 광고 포함).

### 3.4. 시스템 관리 도구
- **볼륨 제어**: [EarTrumpet](https://apps.microsoft.com/detail/9nblggh516xp) (앱별 볼륨 조절, MS 스토어)
- **파일 검색**: [Everything](https://www.voidtools.com/ko-kr/downloads/) (압도적인 속도의 로컬 파일 검색)
- **디스크 관리**: [TreeSize Free](https://www.jam-software.com/treesize) (폴더 용량 시각화)
- **뱅킹 보안앱 삭제**: [구라제거기](https://teus.me/hoaxeliminator/HoaxEliminator7.45/) (PC 느려짐 주범 제거)
- **프린터**: [모두의 프린터](https://modu-print.com/모두의-프린터-다운로드/) (가상 프린터 설정)

---

## 📝 4. 오피스 및 생산성 (Office & Productivity)

### 4.1. Microsoft 365 (Microsoft Store)
학교 계정(Education)을 활용하면 **최신 오피스 프로그램(Word, Excel, PPT 등)**을 무료로 설치할 수 있습니다.
1. **Microsoft Store** 실행 -> **Microsoft 365 (Office)** 검색 및 설치.
2. 앱 실행 후 **학교 계정**으로 로그인.

### 4.2. 한글(HWP) 문서 작업

#### 네이버 MYBOX
한컴오피스를 설치하지 않아도 웹에서 HWP/HWPX 문서를 편집할 수 있습니다.

- **[네이버 MYBOX](https://mybox.naver.com/)**
    - 문서를 MYBOX에 업로드
    - 한컴오피스 Web으로 열어 편집
    - 인터넷 연결 필요

#### 공공 한글
공공기관 민원 서식을 작성하는 용도라면 한컴에서 제공하는 **공공 한글**을 사용할 수 있습니다.

- **[공공 한글](https://download.hancom.com/support/downloadCenter/pubHwp)**

> 예전에 제공되던 **공공서식 한글**은 서비스가 종료되었으며 현재는 **공공 한글**이 제공됩니다.

> 공공 한글은 공공기관 민원 서식 작성 등 지정된 용도를 위한 프로그램이므로 일반적인 한컴오피스 대체 프로그램으로 사용하는 용도와는 다릅니다.

#### rhwp (오픈소스 프로젝트)
HWP/HWPX 파일을 다루는 오픈소스 프로젝트도 개발되고 있습니다.

- **[rhwp GitHub](https://github.com/edwardkim/rhwp)**
    - Rust + WebAssembly 기반
    - HWP / HWPX 뷰어 및 에디터
    - 웹, CLI, VS Code 확장 등 다양한 형태를 목표로 개발 중
    - MIT License

> rhwp는 한글과컴퓨터의 공식 프로그램이 아닌 **독립적인 오픈소스 프로젝트**이며 현재도 개발이 진행 중입니다. 복잡한 문서의 완전한 레이아웃 호환성이 중요한 경우에는 한컴오피스나 한컴오피스 Web 등을 우선 사용하는 것이 안전합니다.

---

## 🎬 5. 미디어 및 보안 (Media & Security)

### 5.1. 동영상 플레이어
- **[팟플레이어](https://tv.kakao.com/guide/potplayer)**
    - **설정 팁**: `F5`(환경설정) -> `소리` -> **[ ] 노멀라이저 사용** 체크 해제 (음질 왜곡 방지)

### 5.2. 보안 및 악성코드 제거 (Security)
윈도우 기본 보안(Defender)을 메인으로 사용하되, 랜섬웨어 방지와 악성코드 제거를 위한 필수 보조 도구를 조합합니다.

- **[AppCheck (앱체크)](https://www.checkmal.com/product/appcheck/#anchor-Compare)**: 랜섬웨어 방어 특화 도구.
    - **⚠️ 라이센스 주의 (중요)**: 이 프로그램은 **오직 '개인(가정)' 사용자에게만 무료**입니다.
    - **학교, 기업, 관공서, PC방 등에서는 무료 사용이 불가능**하므로 설치 시 주의하세요.

- **[Malware Zero (멀웨어 제로)](https://malzero.xyz/)**: 비설치형 악성코드/애드웨어 제거 도구.
    - **필수 유틸리티**: 갑자기 알 수 없는 광고 창이 뜨거나 PC가 느려질 때 가장 효과적입니다. (구 MZK)

- **[VirusTotal](https://www.virustotal.com/gui/home/upload)**: 의심스러운 파일은 실행 전 반드시 업로드하여 교차 검증.

---

## 🎨 6. 폰트 및 디자인 (Fonts & Design)

### 6.1. 상업용 무료 폰트 (눈누)
PPT, 과제, 영상 제작 시 저작권 걱정 없는 무료 폰트를 모아둔 사이트입니다.
- **[눈누 (Noonnu)](https://noonnu.cc/)**: 미리보기 텍스트를 입력해서 여러 폰트를 한눈에 비교할 수 있습니다.
    - **추천 폰트**:
        - **본문용**: 프리텐다드(Pretendard), 나눔스퀘어 네오
        - **제목/강조용**: Gmarket Sans(지마켓 산스), 여기어때 잘난체
    - **설치 팁**: 다운로드한 폰트 파일(`.ttf` or `.otf`) 우클릭 -> **'모든 사용자용으로 설치'** (그래야 PPT 등에서 안 깨짐)

### 6.2. 시스템 UI 개선
- **[Microsoft PowerToys](https://github.com/microsoft/PowerToys)**: MS 공식 파워유저용 툴.
    - **FancyZones**: 화면 분할(레이아웃)을 내 맘대로 커스텀.
    - **Color Picker**: `Win` + `Shift` + `C`로 화면 내 모든 색상 코드 추출.

---

> 🚀 **설치 후 최적화 가이드**: 윈도우 개인 설정, 광고 차단, 한글 로고 팁 등 디테일한 세팅은 **[👉 POST_INSTALL.md](./POST_INSTALL.md)** 파일에서 확인하세요!
