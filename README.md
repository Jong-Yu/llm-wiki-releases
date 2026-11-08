# LLM Wiki 설치 안내

[최신 릴리스와 다운로드](https://github.com/Jong-Yu/llm-wiki-releases/releases/latest) · [소스 코드와 상세 안내](https://github.com/Jong-Yu/llm-wiki)

앱 버전은 **0.1.0**, 게시 태그는 **app-0.1.0**입니다. 이 저장소는 앱 설치 파일과 자동 업데이트 정보를 배포합니다.

## 내 컴퓨터에 맞는 파일

| 운영체제 | 설치 파일 | 추가 준비 |
| --- | --- | --- |
| Windows x64 | [LLM-Wiki-Setup-0.1.0.exe](https://github.com/Jong-Yu/llm-wiki-releases/releases/download/app-0.1.0/LLM-Wiki-Setup-0.1.0.exe) | AI용 Codex 또는 Claude Code 설치·로그인 |
| macOS Apple Silicon(M1·M2·M3 등) | [LLM-Wiki-0.1.0.dmg](https://github.com/Jong-Yu/llm-wiki-releases/releases/download/app-0.1.0/LLM-Wiki-0.1.0.dmg) | AI용 CLI·개인 실행기·Python 준비 |
| macOS ZIP을 원하는 경우 | [LLM-Wiki-0.1.0.zip](https://github.com/Jong-Yu/llm-wiki-releases/releases/download/app-0.1.0/LLM-Wiki-0.1.0.zip) | DMG와 같은 앱 |

이번 배포는 Windows x64와 Mac Apple Silicon용입니다. Intel Mac과 Linux 설치 파일은 포함하지 않습니다. `latest*.yml`과 `.blockmap` 파일은 자동 업데이트용이므로 직접 설치하지 않습니다.

## Windows 설치

1. 위의 Windows 설치 EXE를 내려받아 실행합니다.
2. 설치 마법사에서 설치 폴더를 확인하고 현재 사용자 계정으로 설치합니다.
3. 설치가 끝나면 **LLM Wiki**를 실행합니다.
4. 아래 **첫 실행과 로그인**을 진행합니다.

Python·필수 패키지·Tesseract와 한국어/영어 OCR 데이터가 설치 EXE에 포함돼 있습니다. Windows에서는 별도 Python, OCR, 개인 실행기 ZIP을 설치할 필요가 없습니다. AI CLI는 별도로 준비합니다.

현재 EXE는 코드 서명이 없습니다. Windows에서 보안 확인 메시지가 나오면 이 저장소에서 받은 파일인지 확인하고 OS 안내에 따라 진행 여부를 결정합니다. 보안 기능을 일괄 해제하지 않습니다.

## macOS 앱 설치

1. Apple Silicon용 DMG를 내려받아 엽니다.
2. **LLM Wiki.app**을 **Applications(응용 프로그램)** 폴더로 드래그합니다.
3. 복사가 끝나면 DMG를 꺼내고 응용 프로그램 폴더의 **LLM Wiki**를 실행합니다.
4. ZIP을 받은 경우에도 압축을 푼 앱을 응용 프로그램 폴더로 옮긴 뒤 실행합니다.

현재 Mac 앱은 Developer ID 서명·공증이 없습니다. 열기가 차단됐을 때 출처를 확인하고 실행하기로 결정했다면, 실행을 시도한 뒤 **시스템 설정 → 개인정보 보호 및 보안**의 해당 앱 열기 항목을 확인합니다. [Apple의 안내](https://support.apple.com/en-by/102445)를 따르며 시스템 전체의 보안 기능을 해제하지 않습니다.

### macOS에서 AI 기능 준비

앱 설치와 개인 AI 실행 환경 준비는 별도입니다. 문서와 근거 조회 후 AI 질문·분석을 사용하려면 다음을 준비합니다.

1. [Python 공식 배포](https://www.python.org/downloads/macos/)에서 Python을 준비합니다. 이 프로젝트는 **Python 3.12 이상**을 요구하며, 이번 Mac 환경 검증은 Python 3.12 기준입니다. 기존 `python3`가 조건을 만족하는지 `python3 --version`으로 확인합니다.
2. 같은 릴리스의 [llm-wiki-personal-runtime-0.1.0.zip](https://github.com/Jong-Yu/llm-wiki-releases/releases/download/app-0.1.0/llm-wiki-personal-runtime-0.1.0.zip)을 내려받아 사용자 소유의 계속 사용할 폴더에 압축을 풉니다.
3. 터미널에서 압축 내부의 **llm-wiki-personal-runtime** 폴더로 이동한 뒤 실행합니다.

   ```sh
   python3 -m tools.setup_runtime --role personal
   ```

   설치한 Python 명령이 `python3.13`이라면 위 명령의 `python3` 자리에 그 명령을 사용합니다. 설치 과정에는 인터넷 연결이 필요하며 해당 폴더 안에 `.venv`를 만듭니다.

4. 앱의 개인 실행 환경 고급 설정에서 **프로젝트 폴더**를 위 내부 폴더로, **Python 실행 파일**을 그 안의 **.venv/bin/python**으로 선택합니다.
5. 아래 AI CLI 준비를 마친 후 **실행 준비 확인 → 설정 저장 → 앱 재시작**을 진행합니다.

스캔 PDF·이미지 OCR을 사용하는 Mac에는 Tesseract와 한국어/영어 언어 데이터를 별도로 준비합니다. 준비 여부는 앱의 실행 준비 확인에서 확인합니다. 실행기 ZIP 안의 `INSTALL.txt`와 [프로젝트 실행 안내](https://github.com/Jong-Yu/llm-wiki#python-실행-환경)도 참고할 수 있습니다.

## 첫 실행과 로그인

1. 운영 담당자에게 접속할 **자료 서버 주소**를 받습니다. 원격 서버에는 HTTPS 주소를 사용합니다.
2. 앱 로그인 화면에서 **이름과 서버 주소**를 입력해 가입하거나 로그인합니다.
3. 연결된 작업 공간을 확인하고 문서 목록을 엽니다.

앱 설치 파일에는 운영 서버나 사용자 문서가 들어 있지 않습니다. 별도 서버 준비가 필요한 경우 [소스 저장소의 서버 안내](https://github.com/Jong-Yu/llm-wiki)를 따릅니다.

### AI CLI 준비 — Windows·macOS 공통

1. 사용할 [Codex CLI](https://learn.chatgpt.com/docs/codex/cli) 또는 [Claude Code](https://code.claude.com/docs/en/setup)를 해당 공식 안내에 따라 설치하고 개인 계정으로 로그인합니다.
2. 앱의 **연결 설정 → AI 실행**에서 같은 제공자를 선택합니다.
3. 자동 검색 결과를 확인하고 **실행 준비 확인**을 실행합니다. 찾지 못하면 고급 설정에서 CLI 경로를 선택합니다.
4. 설정을 저장하고 앱을 재시작합니다.

앱 로그인과 AI CLI 로그인은 별개입니다. 기존 Windows에서 외부 Python 경로를 저장했다면 새 설치 파일이 그 설정을 자동으로 바꾸지 않습니다.

## 기존 앱 업데이트

- 진행 중인 AI·변환 작업이 끝났거나 취소됐는지 확인하고 앱을 종료한 뒤 교체합니다. 사용자 자료 폴더나 서버 자료를 지우지 않습니다.
- 이전 업데이트 주소를 내장한 앱 또는 이미 같은 **0.1.0**을 설치한 경우에는 이번 설치 파일로 **한 번 수동 교체**합니다. 같은 버전끼리는 자동 교체되지 않습니다.
- 이후 더 높은 버전이 게시되면 앱이 시작 시와 4시간마다 이 배포 저장소를 조회합니다. 내려받기가 끝나면 재시작 설치를 안내합니다.
- macOS 자동 설치에는 코드 서명이 필요하므로 현재 미서명 Mac 배포는 수동 교체합니다. [Electron의 macOS 업데이트 조건](https://www.electronjs.org/docs/latest/api/auto-updater#macos)을 참고하세요.
- Windows는 같은 사용자 계정으로 새 설치 EXE를 실행하면 됩니다. 포함된 Python·OCR도 앱과 함께 갱신됩니다. 실제 Windows 기기의 자동 업데이트 설치 전체는 아직 검증하지 않았습니다.
- Mac 개인 실행기도 갱신할 때는 같은 릴리스의 새 ZIP을 별도 폴더에 풀어 준비하고, 앱에 새 폴더와 Python 경로를 저장합니다. `--upgrade`만으로 새 실행기 소스를 내려받지는 않습니다.

## 문제 확인

서버 연결 문제는 서버 주소와 접속 가능 여부를 먼저 확인합니다. AI 실행 문제는 CLI 개인 로그인과 앱의 실행 준비 확인 결과를 확인합니다. 설치·갱신 중에는 기존 자료·이력·인증 파일을 임의로 삭제하지 않습니다.
