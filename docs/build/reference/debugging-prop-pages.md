---
description: '자세한 정보: c + + 디버깅 속성 페이지'
title: C + + 디버깅 속성 페이지
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 78115a6b-3799-4515-814e-8566b5bdc55d
f1_keywords:
- VC.Project.IVCLocalDebugPageObject.Command
- VC.Project.IVCLocalDebugPageObject.CommandArguments
- VC.Project.IVCLocalDebugPageObject.WorkingDirectory
- VC.Project.IVCLocalDebugPageObject.Attach
- VC.Project.IVCLocalDebugPageObject.DebuggerType
- VC.Project.IVCLocalDebugPageObject.Environment
- VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCLocalDebugPageObject.EnvironmentMerge
- VC.Project.IVCLocalDebugPageObject.SQLDebugging
- VC.Project.IVCLocalDebugPageObject.AmpDefaultAccelerator
- VC.Project.IVCRemoteDebugPageObject.RemoteCommand
- VC.Project.IVCRemoteDebugPageObject.CommandArguments
- VC.Project.IVCRemoteDebugPageObject.WorkingDirectory
- VC.Project.IVCRemoteDebugPageObject.RemoteMachine
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCRemoteDebugPageObject.DebuggerType
- VC.Project.IVCRemoteDebugPageObject.Environment
- VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCRemoteDebugPageObject.Attach
- VC.Project.IVCRemoteDebugPageObject.SQLDebugging
- VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory
- VC.Project.IVCRemoteDebugPageObject.AdditionalFiles
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCRemoteDebugPageObject.AmpDefaultAccelerator
- VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl
- VC.Project.VCDebugSettings.WebBrowser.DebuggerType
- VC.Project.IVCWebSvcDebugPageObject.HttpUrl
- VC.Project.IVCWebSvcDebugPageObject.DebuggerType
- VC.Project.IVCWebSvcDebugPageObject.SQLDebugging
ms.openlocfilehash: 16a7fec317485dd20a430baab9a413586f913fa3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201744"
---
# <a name="c-debugging-property-pages"></a>C + + 디버깅 속성 페이지

이러한 속성 페이지는 **프로젝트**  >  **속성**  >  **구성 속성**  >  **디버깅** 아래에 있습니다. 드롭다운 컨트롤에서 디버거 형식을 선택 합니다. C + + 코드를 디버깅 하는 방법에 대 한 자세한 내용은 [자습서: Visual Studio를 사용 하 여 c + + 코드 디버그](/visualstudio/debugger/getting-started-with-the-debugger-cpp) 및 [네이티브 코드 디버깅](/visualstudio/debugger/debugging-native-code)을 참조 하세요.

## <a name="local-windows-debugger-property-page"></a>로컬 Windows 디버거 속성 페이지

### <a name="command"></a>명령

실행할 디버그 명령입니다.

### <a name="command-arguments"></a>명령 인수

응용 프로그램에 전달할 명령줄 인수입니다.

### <a name="working-directory"></a>작업 디렉터리

응용 프로그램의 작업 디렉터리입니다. 기본적으로 프로젝트 파일을 포함 하는 디렉터리입니다.

### <a name="attach"></a>연결

디버깅이 시작 될 때 디버거가 기존 프로세스에 연결을 시도할지 여부를 지정 합니다.

### <a name="debugger-type"></a>디버거 형식

사용할 디버거 형식을 지정 합니다. Auto로 설정 된 경우 exe 파일의 내용에 따라 디버거 형식이 선택 됩니다.

**Choices**

- **네이티브 전용** -네이티브 전용
- **관리 전용** -관리 전용
- **혼합** -혼합
- **자동** 자동
- **스크립트** -스크립트
- **Gpu 전용 (C++ AMP)** -gpu만 (C++ AMP)

### <a name="environment"></a>환경

디버깅할 프로그램의 환경 또는 기존 환경과 병합할 변수를 지정 합니다.

### <a name="debugging-accelerator-type"></a>디버깅 액셀러레이터 키 형식

GPU 코드를 디버깅 하는 데 사용할 디버깅 액셀러레이터 키 형식입니다. (GPU 디버거가 활성화 되어 있을 때 사용할 수 있음)

### <a name="gpu-default-breakpoint-behavior"></a>GPU 기본 중단점 동작

GPU 디버거가 중단 되는 빈도를 설정 합니다.

**Choices**

- 휘기 당 **한 번 중단** -휘기 당 한 번 중단
- 모든 스레드에 대해 **중단** (예: cpu 동작)

### <a name="merge-environment"></a>환경 병합

지정 된 환경 변수를 기존 환경과 병합 합니다.

### <a name="sql-debugging"></a>SQL 디버깅

SQL 디버거를 연결 합니다.

### <a name="amp-default-accelerator"></a>Amp 기본 액셀러레이터

C++ AMP의 기본 액셀러레이터 키 선택을 재정의 합니다. 관리 코드를 디버깅할 때는 속성이 적용 되지 않습니다.

## <a name="remote-windows-debugger-property-page"></a>원격 Windows 디버거 속성 페이지

원격 디버깅에 대 한 자세한 내용은 [Visual Studio에서 Visual C++ 프로젝트 원격 디버깅](/visualstudio/debugger/remote-debugging-cpp)을 참조 하세요.

### <a name="remote-command"></a>원격 명령

실행할 디버그 명령입니다.

### <a name="remote-command-arguments"></a>원격 명령 인수

응용 프로그램에 전달할 명령줄 인수입니다.

### <a name="working-directory"></a>작업 디렉터리

응용 프로그램의 작업 디렉터리입니다. 기본적으로 프로젝트 파일을 포함 하는 디렉터리입니다.

### <a name="remote-server-name"></a>원격 서버 이름

원격 서버 이름을 지정 합니다.

### <a name="connection"></a>연결

연결 유형을 지정 합니다.

**Choices**

- **Windows 인증을 사용 하는 원격** - [windows 인증](/windows-server/security/windows-authentication/windows-authentication-overview)을 사용 하는 원격
- **인증을 사용 하지 않는 원격** -인증을 사용 하지 않는 원격

### <a name="debugger-type"></a>디버거 형식

사용할 디버거 형식을 지정 합니다. Auto로 설정 된 경우 exe 파일의 내용에 따라 디버거 형식이 선택 됩니다.

**Choices**

- **네이티브 전용** -네이티브 전용
- **관리 전용** -관리 전용
- **혼합** -혼합
- **자동** 자동
- **스크립트** -스크립트
- **Gpu 전용 (C++ AMP)** -gpu만 (C++ AMP)

### <a name="environment"></a>환경

디버깅할 프로그램의 환경 또는 기존 환경과 병합할 변수를 지정 합니다.

### <a name="debugging-accelerator-type"></a>디버깅 액셀러레이터 키 형식

GPU 코드를 디버깅 하는 데 사용할 디버깅 액셀러레이터 키 형식입니다. (GPU 디버거가 활성화 되어 있을 때 사용할 수 있음)

### <a name="gpu-default-breakpoint-behavior"></a>GPU 기본 중단점 동작

GPU 디버거가 중단 되는 빈도를 설정 합니다.

**Choices**

- 휘기 당 **한 번 중단** -휘기 당 한 번 중단
- 모든 스레드에 대해 **중단** (예: cpu 동작)

### <a name="attach"></a>연결

디버깅이 시작 될 때 디버거가 기존 프로세스에 연결을 시도할지 여부를 지정 합니다.

### <a name="sql-debugging"></a>SQL 디버깅

SQL 디버거를 연결 합니다.

### <a name="deployment-directory"></a>배포 디렉터리

원격 컴퓨터에서 디버깅할 때 프로젝트 출력의 내용 (PDB 파일 제외)을 원격 컴퓨터로 복사 하려면 여기에 경로를 지정 합니다.

### <a name="additional-files-to-deploy"></a>배포할 추가 파일

원격 컴퓨터에서 디버그할 때 여기에 지정 된 파일 및 디렉터리 (프로젝트 출력 외)가 지정 된 경우 배포 디렉터리에 복사 됩니다.

### <a name="deploy-visual-c-debug-runtime-libraries"></a>Visual C++ 디버그 런타임 라이브러리

활성 플랫폼 (Win32, x64 또는 ARM)의 디버그 런타임 라이브러리를 배포할지 여부를 지정 합니다.

### <a name="amp-default-accelerator"></a>Amp 기본 액셀러레이터

C++ AMP의 기본 액셀러레이터 키 선택을 재정의 합니다. 관리 코드를 디버깅할 때는 속성이 적용 되지 않습니다.

## <a name="web-browser-debugger-property-page"></a>웹 브라우저 디버거 속성 페이지

### <a name="http-url"></a>HTTP URL

프로젝트에 대 한 URL을 지정 합니다.

### <a name="debugger-type"></a>디버거 형식

사용할 디버거 형식을 지정 합니다. Auto로 설정 된 경우 exe 파일의 내용에 따라 디버거 형식이 선택 됩니다.

**Choices**

- **네이티브 전용** -네이티브 전용
- **관리 전용** -관리 전용
- **혼합** -혼합
- **자동** 자동
- **스크립트** -스크립트

## <a name="web-service-debugger-property-page"></a>웹 서비스 디버거 속성 페이지

### <a name="http-url"></a>HTTP URL

프로젝트에 대 한 URL을 지정 합니다.

### <a name="debugger-type"></a>디버거 형식

사용할 디버거 형식을 지정 합니다. Auto로 설정 된 경우 exe 파일의 내용에 따라 디버거 형식이 선택 됩니다.

**Choices**

- **네이티브 전용** -네이티브 전용
- **관리 전용** -관리 전용
- **혼합** -혼합
- **자동** 자동
- **스크립트** -스크립트

### <a name="sql-debugging"></a>SQL 디버깅

SQL 디버거를 연결 합니다.
