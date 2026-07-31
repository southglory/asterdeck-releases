# Asterdeck 설치 안내

사용자가 고를 설치 파일은 하나입니다. 최신 Release의
`Asterdeck_*_setup-kit.zip`을 받아 압축을 풀고 `asterdeck-setup`을 실행합니다.

## 설치 전에

- Codex를 쓸 컴퓨터에는 Codex CLI가 설치되고 로그인되어 있어야 합니다.
- Claude를 쓸 컴퓨터에는 Claude Code가 설치되고 로그인되어 있어야 합니다.
- Asterdeck은 제공자의 로그인 정보나 대화 데이터베이스를 복사하지 않습니다.

## 1. Setup Kit 받기

[Asterdeck Releases](https://github.com/southglory/asterdeck-releases/releases)에서
같은 버전의 다음 두 파일을 받습니다.

```text
Asterdeck_VERSION_setup-kit.zip
Asterdeck_VERSION_setup-kit.zip.sha256
```

파일 이름의 `VERSION`은 받은 Release 버전으로 바꿉니다.

Windows PowerShell:

```powershell
$zip = "Asterdeck_VERSION_setup-kit.zip"
$expected = ((Get-Content "$zip.sha256" -Raw).Trim() -split "\s+")[0]
$actual = (Get-FileHash $zip -Algorithm SHA256).Hash
if ($actual.ToLower() -ne $expected.ToLower()) { throw "체크섬 불일치" }
Expand-Archive $zip -DestinationPath .
Set-Location .\asterdeck-setup-kit
```

Linux:

```bash
sha256sum --check Asterdeck_VERSION_setup-kit.zip.sha256
python3 -m zipfile -e Asterdeck_VERSION_setup-kit.zip .
cd asterdeck-setup-kit
```

SHA-256은 다운로드 파일의 무결성 검사이며 코드 서명을 대신하지는 않습니다.
현재 Windows 설치 프로그램은 초기 배포 단계의 미서명 패키지이므로
SmartScreen 경고가 나타날 수 있습니다.

## 2. 설치 계획 확인

기본 실행은 변경 예정 항목만 보여주며 컴퓨터를 바꾸지 않습니다.

Windows PowerShell:

```powershell
.\asterdeck-setup
```

Linux:

```bash
sh ./asterdeck-setup
```

## 3. 설치

Windows:

```powershell
.\asterdeck-setup --yes
```

Linux:

```bash
sh ./asterdeck-setup --yes
```

설치기는 다음 역할을 자동 선택합니다.

- Windows: 데스크톱 앱과 `asterdeck` CLI
- GUI가 있는 Ubuntu 24.04 x86_64: 데스크톱 앱과 CLI
- GUI가 없는 Ubuntu 24.04 x86_64: CLI와 로컬 Session Host

서버 역할을 명시하려면 `--headless`, 데스크톱 역할을 명시하려면
`--desktop`을 추가합니다. Setup Kit 바이너리는 Windows x64와 Ubuntu 24.04
x86_64를 지원하며, 다른 Linux 배포판과 Ubuntu 버전은 현재 지원하지
않습니다.

## 4. 확인과 업데이트

새 터미널에서 다음을 실행합니다.

```bash
asterdeck doctor
```

업데이트할 때도 새 Setup Kit에서 같은 `asterdeck-setup --yes` 명령을
실행합니다. 사용자 설정과 Session Passport를 보존하기 위해 기존 버전을
먼저 제거하지 않습니다.
