# Asterdeck Releases

Asterdeck의 공식 공개 배포 저장소입니다. 비공개 제품 소스나 개발 기록은
포함하지 않으며, 사용자가 필요한 설치 파일·SHA-256 체크섬·Setup Kit·설치
안내만 제공합니다.

## 가장 쉬운 설치

1. [Asterdeck Releases](https://github.com/southglory/asterdeck-releases/releases)
   에서 가장 높은 버전의 다음 두 파일을 받습니다.

   ```text
   Asterdeck_VERSION_setup-kit.zip
   Asterdeck_VERSION_setup-kit.zip.sha256
   ```

2. [INSTALL.md](INSTALL.md)에 따라 체크섬을 확인하고 `asterdeck-setup`을
   실행합니다.

설치기는 Windows와 Ubuntu 24.04, GUI 유무를 확인해 데스크톱 앱·CLI·로컬
Session Host 중 필요한 항목을 자동으로 선택합니다.

## 포함되는 배포 파일

- Windows x64 설치 프로그램과 독립 실행형 CLI
- Ubuntu 24.04 x86_64 AppImage, Debian 패키지와 독립 실행형 CLI
- Windows와 Ubuntu 24.04에서 함께 사용하는 Setup Kit
- 모든 payload의 SHA-256 체크섬

Asterdeck는 Apache License 2.0으로 배포됩니다. 자세한 조건은 [LICENSE](LICENSE)
와 Release에 포함된 `NOTICE`를 확인하세요.
