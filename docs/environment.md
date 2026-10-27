# 프로젝트 환경 및 버전 명세

최종 확인: 2026-10-27 (Asia/Seoul)

이 문서는 fishing 개발 PC에서 확인한 도구 버전과 프로젝트의 버전 지정 상태를 기록합니다.
현재 설치된 버전은 관측값이며, 프로젝트의 최소 요구 버전이나 호환성 검증 결과를 뜻하지 않습니다.
이번 점검에서는 프로그램 설치·업데이트와 프로젝트 설정 변경을 진행하지 않았습니다.

## 1. 프로젝트 기본 정보

| 항목 | 내용 |
| --- | --- |
| 프로젝트명 | `fishing` |
| 제품 | 출조노트 모바일 앱 |
| 프로젝트 및 Git 루트 | `C:\fishing` |
| 확인 당시 브랜치 | `main` |
| 개발 방향 | React Native + Expo |
| 대상 플랫폼 | Android, iOS |
| 현재 단계 | 요구사항 정의, 앱 초기화 전 |

## 2. 확인된 개발 PC 환경

| 항목 | 확인된 버전 또는 값 | 확인 방법 |
| --- | --- | --- |
| 운영체제 | Microsoft Windows 11 Home | `Get-CimInstance Win32_OperatingSystem` |
| Windows 버전 | `10.0.26300` | 위 명령의 `Version` |
| Windows 빌드 | `26300` | 위 명령의 `BuildNumber` |
| OS 아키텍처 | 64비트 / x64 | OS 정보 및 런타임 정보 |
| PowerShell | `7.6.5` / `Core` | `$PSVersionTable` |
| Node.js | `v24.22.1` / x64 | `node -v`, `node -p "process.arch"` |
| npm | `11.19.1` | `npm -v` |
| Git | `2.45.1.windows.1` | `git --version` |
| VS Code | `1.96.3` / x64 | `code --version` |

버전 조회 명령은 정상 응답했습니다. Expo 앱 실행, 의존성 설치, Android·iOS 빌드는
아직 검증하지 않았습니다. 위 버전으로 앱 개발이 검증되었다는 의미는 아닙니다.

### 명령어 경로

아래 경로는 이 PC의 설치 위치이며 다른 개발 PC에서 동일할 필요는 없습니다.

| 명령 | 확인된 경로 |
| --- | --- |
| `node` | `C:\Program Files\nodejs\node.exe` |
| `npm` | `C:\Program Files\nodejs\npm.ps1` |
| `git` | `C:\Program Files\Git\cmd\git.exe` |
| `code` | `C:\Users\INJUNG\AppData\Local\Programs\Microsoft VS Code\bin\code.cmd` |

## 3. 앱 패키지 및 버전 지정 상태

| 항목 | 현재 상태 | 버전을 기록할 근거 |
| --- | --- | --- |
| Expo SDK / `expo` | 미정 · 프로젝트에 설치되지 않음 | 초기화 후 `package.json`, `package-lock.json` |
| React Native / `react-native` | 미정 · 프로젝트에 설치되지 않음 | 위 파일 |
| React / `react` | 미정 · 프로젝트에 설치되지 않음 | 위 파일 |
| TypeScript 사용 여부 및 버전 | 미정 | 사용 결정 후 `package.json`, `package-lock.json` |
| 라우팅·상태 관리·저장소 패키지 | 미정 | 기능 및 기술 설계 확정 후 기록 |
| 프로젝트가 지정하는 Node.js 버전 | 아직 지정하지 않음 | 채택 시 `.nvmrc` 또는 `.node-version`, 필요 시 `engines` |
| 프로젝트가 지정하는 npm 버전 | 아직 지정하지 않음 | 채택 시 `packageManager` 등 프로젝트 설정 |
| 앱 버전·Android 빌드 번호·iOS 빌드 번호 | 미정 | 생성 후 Expo 앱 설정 |

확인 당시 `package.json`, `package-lock.json`, `app.json`, `app.config.*`,
`.nvmrc`, `.node-version`, `.npmrc`, `eas.json`은 프로젝트에 없었습니다.
따라서 현재는 의존성 버전이나 앱 빌드 설정이 고정되어 있지 않습니다.

## 4. 모바일 개발 관련 도구 확인 범위

| 항목 | 확인 결과 | 추가 확인 사항 |
| --- | --- | --- |
| Java | PATH에서 `java` 명령 발견 | `java -version`이 응답하지 않아 중단함. 버전·정상 실행 여부 미확인 |
| Java 컴파일러 | PATH에서 `javac` 명령 발견 | 버전·정상 실행 여부 미확인 |
| Android Debug Bridge | PATH에서 `adb` 명령을 찾지 못함 | 설치 위치 및 PATH 등록 여부 미확인 |
| Android 에뮬레이터 CLI | PATH에서 `emulator` 명령을 찾지 못함 | 설치 위치 및 PATH 등록 여부 미확인 |
| Android Studio / Android SDK | 이번 점검에서 설치 여부를 확인하지 않음 | 개발·빌드 방식 결정 후 확인 |
| Expo CLI / EAS CLI | PATH에서 `expo`, `eas` 명령을 찾지 못함 | 프로젝트 또는 필요 시 실행하는 도구의 버전은 별도 확인 필요 |
| iOS 개발·빌드 환경 | 미확인 | 빌드·배포 방식과 함께 정리 |

PATH에서 명령을 찾지 못한 것은 미설치를 확정하는 근거가 아닙니다.
Java 관련 명령은 `C:\Program Files\Common Files\Oracle\Java\javapath\`에서 발견했으며,
이 경로만으로 사용할 JDK의 버전이나 Android 빌드 적합성을 판단하지 않습니다.

## 5. 앱 초기화 시 확정할 항목

- 채택할 Expo SDK와 이에 맞는 React Native·React 버전
- 해당 구성에서 지원하는 Node.js 버전과 프로젝트에서 사용할 npm 버전
- 언어, 라우팅 등 초기 프로젝트 구성
- Android·iOS 실행 및 빌드 방식과 필요한 도구 버전
- 각 플랫폼에서의 실행 검증 결과

버전 선택 시 공식 문서의 지원 범위를 확인하고, 실제 생성된 설정·잠금 파일을 기준으로
이 문서를 갱신합니다. 버전이 아직 정해지지 않은 도구의 설치를 이 문서만으로 요구하지 않습니다.

## 6. 버전 기록 및 갱신 방법

1. 도구나 패키지 버전을 변경하면 변경 날짜, 이유와 검증 결과를 기록합니다.
2. 의존성 선언은 `package.json`, 실제 잠긴 버전은 `package-lock.json`을 기준으로 확인합니다.
3. 프로젝트의 버전 설정과 개발 PC의 관측값을 구분해 유지합니다.
4. 앱 실행·빌드를 수행하면 명령, 플랫폼, 성공 여부를 기록합니다.
5. 다른 PC에서도 필요한 환경을 재현할 수 있도록 초기화 후 README에 설치·실행 절차를 추가합니다.

### 기본 버전 재확인 명령

프로젝트 루트에서 PowerShell로 실행합니다. 아래 명령은 패키지를 설치하지 않습니다.

```powershell
node -v
npm -v
git --version
code --version
$PSVersionTable.PSVersion.ToString()
Get-CimInstance Win32_OperatingSystem | Select-Object Caption, Version, BuildNumber, OSArchitecture
```

## 변경 이력

| 날짜 | 내용 | 검증 범위 |
| --- | --- | --- |
| 2026-10-27 | 최초 작성 | Windows·개발 도구 버전, 프로젝트 설정 파일 유무, 모바일 도구 PATH 조회 |
