---
description: '자세한 정보: 포팅 가이드: MFC Scribble'
title: '포팅 가이드: MFC Scribble'
ms.date: 10/23/2019
ms.assetid: 8ddb517d-89ba-41a1-ab0d-4d2c6d9047e8
ms.openlocfilehash: 46fac5ceaeadd803ff30f2fa3f8e7723d7d6f6f2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322701"
---
# <a name="porting-guide-mfc-scribble"></a>포팅 가이드: MFC Scribble

이 항목은 이전 버전의 Visual Studio에서 만든 Visual Studio C++ 프로젝트를 Visual Studio 2017로 업그레이드하는 절차를 소개하는 여러 항목 중 첫 번째입니다. 이러한 항목에서는 예를 들어 매우 간단한 프로젝트부터 좀더 복잡한 프로젝트로 이동하는 업그레이드 프로세스를 소개합니다. 이 항목에서는 MFC Sribble이라는 특정 프로젝트에 대한 업그레이드 프로세스를 안내합니다. C++ 프로젝트에 대한 업그레이드 프로세스의 기본 사항을 소개하는 데 적합합니다.

각 Visual Studio 버전에는 이전 버전의 Visual Studio에서 최신 버전으로의 코드 이동을 복잡하게 하는 비호환성이 있을 수 있습니다. 코드에 필요한 변경이 있어서 코드를 다시 컴파일하고 업데이트해야 하는 경우도 있고, 프로젝트 파일에 필요한 변경이 있는 경우도 있습니다. 이전 버전의 Visual Studio에서 만든 프로젝트를 여는 경우 Visual Studio에서 프로젝트 또는 솔루션을 최신 버전으로 업데이트할지 여부를 묻는 메시지를 자동으로 표시합니다. 이러한 도구는 일반적으로 프로젝트 파일만 업그레이드하고 소스 코드를 수정하지 않습니다.

## <a name="mfc-scribble"></a>MFC Scribble

MFC Scribble은 다양한 버전의 Visual C++에 포함된 잘 알려진 샘플입니다. MFC의 기본 기능 중 일부를 보여 주는 간단한 그리기 애플리케이션입니다. 관리 코드 및 네이티브 코드 버전을 포함하여 다양한 버전으로 제공됩니다. 이 예제에서는 Visual Studio 2005에서 네이티브 코드로 작성된 이전 버전의 Scribble을 찾아 Visual Studio 2017에서 열었습니다.

업그레이드하기 전에 Windows 데스크톱 작업이 설치되어 있는지 확인합니다. Visual Studio 설치 관리자(vs_installer.exe)를 엽니다. 설치 관리자를 여는 한 가지 방법은 **파일**  >  **새로 만들기 프로젝트** 를 선택 하 고 **열려 있는 Visual Studio 설치 관리자** 표시 될 때까지 설치 된 템플릿 목록의 맨 아래로 스크롤합니다. 설치 관리자를 열면 사용 가능한 작업이 모두 표시됩니다. **Windows 데스크톱** 워크 로드에 대 한 상자를 선택 하지 않은 경우 선택 하 고 창 맨 아래에 있는 **수정** 단추를 클릭 합니다.

다음으로, 전체 솔루션과 해당 콘텐츠를 모두 백업합니다.

마지막으로, 최신 버전의 Visual Studio에서 솔루션을 열고 마법사에서 프로젝트를 변환 하도록 허용 합니다.

마법사를 사용하여 프로젝트를 업그레이드하는 대신 `/Upgrade` 옵션을 사용하여 명령줄에서 devenv를 실행할 수도 있습니다. [/Upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe)를 참조하세요. 이 작업은 다수의 프로젝트에 대해 업그레이드 프로세스를 자동화하는 데 유용할 수 있습니다.

### <a name="step-1-converting-the-project-file"></a>1단계. 프로젝트 파일 변환

Visual Studio에서 이전 프로젝트 파일을 열면 Visual Studio에서 프로젝트 파일을 최신 버전으로 변환 하는 것을 제공 합니다. 다음과 같은 대화 상자가 나타납니다.

![프로젝트 및 솔루션 변경 내용 검토](../porting/media/scribbleprojectupgrade.PNG "프로젝트 및 솔루션 변경 내용 검토")

Itanium 대상을 사용할 수 없어 변환되지 않는다고 알리는 오류가 발생했습니다.

```Output
Platform 'Itanium' is missing from this project. All the configurations and their file configuration settings specific to this platform will be ignored. If you want this platform converted, please make sure you have the corresponding platform installed under '%vctargetpath%\platforms\Itanium'.Continue to convert this project without this platform?
```

이전 Scribble 프로젝트를 만들 때 Itanium은 중요한 대상 플랫폼이었습니다. Windows 플랫폼은 더 이상 Itanium을 지원하지 않으므로 Itanium 플랫폼을 지원하지 않고 계속하도록 선택했습니다.

그런 다음 visual Studio에서 이전 프로젝트 파일의 모든 문제를 나열하는 마이그레이션 보고서를 표시했습니다.

![보고서 업그레이드](../porting/media/scribblemigrationreport.PNG "보고서 업그레이드")

이 경우 문제는 모두 경고였으며, Visual Studio에서 프로젝트 파일을 적절하게 변경했습니다. 프로젝트와 관련해서 가장 큰 차이점은 빌드 도구가 vcbuild에서 msbuild로 변경된 것입니다. 이 변경 내용은 Visual Studio 2010에서 처음 도입되었습니다. 기타 변경 내용에는 프로젝트 파일 자체의 요소 시퀀스 다시 정렬이 포함됩니다. 이 간단한 프로젝트에서 추가로 주의해야 할 문제는 없었습니다.

### <a name="step-2-getting-it-to-build"></a>2단계. 빌드

빌드하기 전에 프로젝트 시스템에서 사용 중인 컴파일러 버전을 알 수 있도록 플랫폼 도구 집합을 확인합니다. 프로젝트 속성 대화 상자의 **구성 속성** 아래, **일반** 범주에서 **플랫폼 도구 집합** 속성을 확인합니다. Visual Studio 버전 및 플랫폼 도구 버전 번호(이 경우 Visual Studio 2017 버전의 도구에 해당하는 v141)이 포함되어 있습니다. 처음에 Visual Studio 2010, 2012, 2013 또는 2015로 컴파일된 프로젝트를 변환 하는 경우 도구 집합이 최신 도구 집합으로 자동으로 업데이트 되지 않습니다.

유니코드로 전환하려면 프로젝트의 속성을 열고 **구성 속성** 아래에서 **일반** 섹션을 선택한 다음 **문자 집합** 속성을 찾습니다. 이 속성을 **멀티바이트 문자 집합 사용** 에서 **유니코드 문자 집합 사용** 으로 변경합니다. 이렇게 변경하면 _UNICODE 및 UNICODE 매크로가 정의되고 _MBCS는 정의되지 않습니다. 이는 속성 대화 상자의 **C/C++** 범주 아래, **명령줄** 속성에서 확인할 수 있습니다.

```Output
/GS /analyze- /W4 /Zc:wchar_t /Zi /Gm- /Od /Fd".\Debug\vc141.pdb" /Zc:inline /fp:precise /D "_AFXDLL" /D "WIN32" /D "_DEBUG" /D "_WINDOWS" /D "_UNICODE" /D "UNICODE" /errorReport:prompt /WX /Zc:forScope /Gd /Oy- /MDd /Fa".\Debug\" /EHsc /nologo /Fo".\Debug\" /Fp".\Debug\Scribble.pch" /diagnostics:classic
```

Scribble 프로젝트는 유니코드 문자를 사용하여 컴파일되도록 설정되지 않았지만 이미 char 대신 TCHAR로 작성되었으므로 실제로 변경해야 할 사항이 없습니다. 프로젝트가 유니코드 문자 집합을 사용하여 성공적으로 빌드됩니다.

이제 솔루션을 빌드하겠습니다. 컴파일러에서 출력 창을 통해 _WINNT32_WINNT가 정의되지 않았다고 알립니다.

```Output
_WIN32_WINNT not defined. Defaulting to _WIN32_WINNT_MAXVER (see WinSDKVer.h)
```

이는 오류가 아니라 경고이며, Visual Studio C++ 프로젝트를 업그레이드할 때 흔히 발생합니다. 애플리케이션이 실행되는 가장 낮은 버전의 Windows를 정의하는 매크로입니다. 경고를 무시하는 경우 현재 버전의 Windows를 의미하는 기본값 _WIN32_WINNT_MAXVER을 수락하는 것입니다. 가능한 값의 테이블은 [Using the Windows Headers](/windows/win32/WinProg/using-the-windows-headers)(Windows 헤더 사용)을 참조하세요. 예를 들어 Vista부터 모든 버전에서 실행되도록 설정할 수 있습니다.

```cpp
#define _WIN32_WINNT _WIN32_WINNT_VISTA
```

코드에서 이 매크로로 지정한 Windows 버전에서 사용할 수 없는 Windows API의 일부를 사용하는 경우 컴파일러 오류로 표시됩니다. Scribble 코드의 경우 오류가 없습니다.

### <a name="step-3-testing-and-debugging"></a>3단계. 테스트 및 디버깅

테스트 도구 모음이 없으므로 앱을 시작하고 UI를 통해 수동으로 해당 기능을 테스트했습니다. 문제가 발견되지 않았습니다.

### <a name="step-4-improve-the-code"></a>4단계. 코드 개선

이제 Visual Studio 2017로 마이그레이션했으므로 새로운 C++ 기능을 활용하기 위해 일부 변경 작업을 수행하는 것이 좋습니다. 현재 버전의 C++ 컴파일러는 이전 버전보다 C++ 표준에 훨씬 더 부합되므로 코드를 더 안전하고 다른 컴파일러 및 운영 체제로 포팅하기 쉽게 변경하려는 경우 몇 가지 향상된 기능을 고려해야 합니다.

## <a name="next-steps"></a>다음 단계

Scribble은 작고 간단한 Windows 데스크톱 애플리케이션이며 변환하기 어렵지 않았습니다. 마찬가지로, 대부분의 작고 간단한 앱은 쉽게 새 버전으로 변환됩니다.  많은 줄의 코드, 최신 엔지니어링 표준에 부합되지 않는 레거시 코드, 여러 프로젝트와 라이브러리, 사용자 지정 빌드 단계를 포함하는 더 복잡한 애플리케이션이나 복잡한 스크립팅된 자동화 빌드의 경우 업그레이드하는 데 더 오랜 시간이 걸립니다. [다음 예제](../porting/porting-guide-com-spy.md)인 COM Spy라는 ATL/COM 애플리케이션으로 계속합니다.

## <a name="see-also"></a>참고 항목

[포팅 및 업그레이드: 예제 및 사례 연구](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[다음 예제: COM Spy](../porting/porting-guide-com-spy.md)
