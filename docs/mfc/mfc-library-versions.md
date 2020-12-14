---
description: '자세한 정보: MFC 라이브러리 버전'
title: MFC 라이브러리 버전
ms.date: 05/08/2019
helpviewer_keywords:
- class libraries [MFC], building versions
- version information [MFC], MFC library
- MFC class library
- MFC class library, building
- MFC libraries
- MFC, library versions
- libraries [MFC], versions
ms.openlocfilehash: 26d17604ec201deffd5fd2d5e843269e67e3dd07
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280588"
---
# <a name="mfc-library-versions"></a>MFC 라이브러리 버전

MFC 라이브러리는 ANSI 싱글바이트 및 MBCS (멀티 바이트 문자 집합) 코드를 지 원하는 버전 뿐만 아니라 유니코드를 지 원하는 버전 (UTF-16LE, Windows 네이티브 문자 집합)에서 사용할 수 있습니다. 각 MFC 버전은 정적 라이브러리나 공유 DLL로 사용할 수 있습니다. 크기가 매우 중요 하 고 이러한 컨트롤을 필요로 하지 않는 응용 프로그램의 경우 대화에 대 한 MFC 컨트롤을 유지 하는 작은 MFC 정적 라이브러리 버전도 있습니다. MFC 라이브러리는 x86, x64 및 ARM 프로세서를 포함 하는 지원 되는 아키텍처에 대 한 디버그 버전과 릴리스 버전 모두에서 사용할 수 있습니다. 모든 버전의 MFC 라이브러리를 사용 하 여 응용 프로그램 (.exe 파일) 및 Dll을 모두 만들 수 있습니다. 또한 관리 코드와의 상호 작용을 위해 컴파일된 MFC 라이브러리 집합도 있습니다. MFC 공유 Dll에는 라이브러리 이진 호환성을 나타내는 버전 번호가 포함 되어 있습니다.

## <a name="automatic-linking-of-mfc-library-versions"></a>MFC 라이브러리 버전 자동 링크

MFC 헤더 파일은 빌드 환경에 정의 된 값에 따라 연결할 MFC 라이브러리의 올바른 버전을 자동으로 결정 합니다. MFC 헤더 파일은 특정 버전의 MFC 라이브러리에서 연결 하도록 링커에 지시 하는 컴파일러 지시문을 추가 합니다.

예를 들면 AFX입니다. H 헤더 파일은 MFC의 전체 정적, 제한 된 정적 또는 공유 DLL 버전에 연결 하도록 링커에 지시 합니다. ANSI/MBCS 또는 유니코드 버전; 빌드 구성에 따라 디버그 또는 일반 정품 버전:

```cpp
#ifndef _AFXDLL
    #ifdef _AFX_NO_MFC_CONTROLS_IN_DIALOGS
        #ifdef _DEBUG
            #pragma comment(lib, "afxnmcdd.lib")
        #else
            #pragma comment(lib, "afxnmcd.lib")
        #endif
        #pragma comment(linker, "/include:__afxNoMFCControlSupportInDialogs")
        #pragma comment(linker, "/include:__afxNoMFCControlContainerInDialogs")
    #endif
    #ifndef _UNICODE
        #ifdef _DEBUG
            #pragma comment(lib, "nafxcwd.lib")
        #else
            #pragma comment(lib, "nafxcw.lib")
        #endif
    #else
        #ifdef _DEBUG
            #pragma comment(lib, "uafxcwd.lib")
        #else
            #pragma comment(lib, "uafxcw.lib")
        #endif
    #endif
#else
    #ifndef _UNICODE
        #ifdef _DEBUG
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "d.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "d.lib")
        #else
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER ".lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER ".lib")
        #endif
    #else
        #ifdef _DEBUG
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "ud.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "ud.lib")
        #else
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "u.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "u.lib")
        #endif
    #endif
#endif
```

Mfc 헤더 파일에는 MFC 라이브러리, Win32 라이브러리, OLE 라이브러리, 샘플에서 빌드된 OLE 라이브러리, ODBC 라이브러리 등을 비롯 한 모든 필수 라이브러리에서 연결할 지시문도 포함 됩니다.

## <a name="ansi-mbcs-and-unicode"></a>ANSI, MBCS 및 유니코드

MFC ANSI/MBCS 라이브러리 버전은 ASCII와 같은 싱글바이트 문자 집합과 Shift-jis와 같은 멀티 바이트 문자 집합을 모두 지원 합니다. MFC 유니코드 라이브러리 버전은 UTF-16LE 와이드 문자로 인코딩된 형식으로 유니코드를 지원 합니다. U t f-8로 인코딩된 유니코드 지원을 위해 MFC의 ANSI/MBCS 라이브러리 버전을 사용 합니다.

IDE에서 싱글바이트, 멀티 바이트 또는 와이드 문자 유니코드 문자열 및 문자 지원을 사용 하도록 프로젝트 구성을 설정 하려면 **프로젝트 속성** 대화 상자를 사용 합니다. **구성 속성**  >  **일반** 페이지에서 **문자 집합** 속성을 **설정 안 함** 으로 설정 하 여 싱글바이트 문자 집합을 사용 하도록 설정 합니다. 멀티 **바이트** 문자 집합을 사용 하도록 속성을 설정 하거나 **유니코드 문자 집합** 을 사용 하 여 u t f-16으로 인코딩된 유니코드를 사용 하도록 설정 합니다.

MFC 프로젝트에서는 전처리기 기호 유니코드를 사용 \_ 하 여 utf-16 와이드 문자 유니코드 지원과 mbcs \_ 지원을 나타내는 mbcs를 사용 합니다. 이러한 옵션은 프로젝트에서 함께 사용할 수 없습니다.

## <a name="mfc-static-library-naming-conventions"></a>MFC 정적 라이브러리 명명 규칙

MFC에 대 한 정적 라이브러리는 다음 명명 규칙을 사용 합니다. 라이브러리 이름의 형식은

> <em>u</em> AFX<em>cd</em>. LIB

여기서 기울임꼴 소문자에 표시 된 문자는 다음 표에 나와 있는 의미를 갖는 지정자에 대 한 자리 표시자입니다.

|지정자|값 및 의미|
|---------------|-------------------------|
|*u*|ANSI/MBCS (N) 또는 유니코드 (U); 대화 상자에서 MFC 컨트롤이 없는 버전을 생략 합니다.|
|*c*|대화 상자에서 MFC 컨트롤을 사용 하는 버전 (CW) 또는 없는 경우 (NMCD)|
|*d*|디버그 또는 릴리스: D = Debug; 릴리스에 대 한 생략 지정자|

다음 표에 나열 된 모든 라이브러리는 지원 되는 빌드 아키텍처에 대 한 \atlmfc\lib 디렉터리에 미리 구성 되어 있습니다.

|라이브러리|설명|
|-------------|-----------------|
|NAFXCW.LIB|MFC Static-Link 라이브러리, 릴리스 버전|
|NAFXCWD.LIB|MFC Static-Link 라이브러리, 디버그 버전|
|UAFXCW. LIB|유니코드를 지 원하는 MFC Static-Link 라이브러리, 릴리스 버전|
|UAFXCWD. LIB|유니코드를 지 원하는 MFC Static-Link 라이브러리, 디버그 버전|
|AFXNMCD. LIB|Mfc 대화 상자 컨트롤이 없는 MFC Static-Link 라이브러리, 릴리스 버전|
|AFXNMCDD. LIB|Mfc 대화 상자 컨트롤이 없는 MFC Static-Link 라이브러리, 디버그 버전|

기본 이름 및 .pdb 확장명을 가진 디버거 파일은 각 정적 라이브러리에도 사용할 수 있습니다.

## <a name="mfc-shared-dll-naming-conventions"></a>MFC 공유 DLL 명명 규칙

MFC 공유 Dll도 구조화 된 명명 규칙을 따릅니다. 이렇게 하면 용도에 따라 사용 해야 하는 DLL 또는 라이브러리를 쉽게 알 수 있습니다.

MFC Dll에는 이진 호환성을 나타내는 *버전* 번호가 있습니다. 다른 라이브러리와 동일한 버전의 MFC Dll 및 컴파일러 도구 집합을 사용 하 여 프로젝트 내에서 호환성을 보장 합니다.

|DLL|설명|
|---------|-----------------|
|MFC *버전* GDIPLUS.DLL|MFC DLL, ANSI 또는 MBCS 릴리스 버전|
|MFC *버전* U.DLL|MFC DLL, 유니코드 릴리스 버전|
|MFC *버전* D.DLL|MFC DLL, ANSI 또는 MBCS 디버그 버전|
|MFC *버전* UD.DLL|MFC DLL, 유니코드 디버그 버전|
|MFCM *버전* 입니다. GDIPLUS.DLL|Windows Forms 컨트롤, ANSI 또는 MBCS 릴리스 버전의 MFC DLL|
|MFCM *버전* U.DLL|Windows Forms 컨트롤, 유니코드 릴리스 버전의 MFC DLL|
|MFCM *버전* D.DLL|Windows Forms 컨트롤, ANSI 또는 MBCS 디버그 버전을 사용 하는 MFC DLL|
|MFCM *버전* UD.DLL|Windows Forms 컨트롤, 유니코드 디버그 버전을 사용 하는 MFC DLL|

이러한 공유 Dll을 사용 하는 응용 프로그램 또는 MFC 확장명 Dll을 빌드하는 데 필요한 가져오기 라이브러리에는 DLL과 동일한 기본 이름이 있지만 .lib 파일 이름 확장명이 있습니다. 공유 Dll을 사용 하는 경우 작은 정적 라이브러리를 여전히 코드와 연결 해야 합니다. 이 라이브러리의 이름은 MFCS *version*{U} {D}. D D}입니다.

응용 프로그램에서 든, MFC 확장명 DLL에서 든 상관 없이 MFC의 공유 DLL 버전에 동적으로 연결 하는 경우 일치 하는 MFC *버전* 을 포함 해야 합니다. 제품을 배포할 때 DLL 또는 MFC *버전* 을U.DLL 합니다.

응용 프로그램과 함께 배포할 수 있는 Visual C++ Dll 목록은 [Microsoft Visual Studio 2017 및 Microsoft Visual Studio 2017 SDK 용 배포 가능 코드 (유틸리티 및 BuildServer 파일 포함)](/visualstudio/productinfo/2017-redistribution-vs) 또는 [Visual Studio 2019 용 배포 가능 코드](/visualstudio/releases/2019/redistribution)를 참조 하세요.

MFC의 MBCS 및 유니코드 지원에 대 한 자세한 내용은 [유니코드 및 mbcs (멀티 바이트 문자 집합) 지원](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)을 참조 하세요.

## <a name="dynamic-link-library-support"></a>동적 연결 라이브러리 지원

정적 또는 공유 동적 MFC 라이브러리를 사용 하 여 MFC 실행 파일이 나 mfc가 아닌 실행 파일에서 사용할 수 있는 Dll을 만들 수 있습니다. 이를 "일반 Dll" 또는 "일반 MFC Dll" 이라고 하며,이를 MFC 응용 프로그램 및 MFC Dll 에서만 사용할 수 있는 MFC 확장명 Dll과 구분할 수 있습니다. Mfc 정적 라이브러리를 사용 하 여 작성 된 DLL을 이전 참조의 USRDLL 라고도 합니다 .이는 MFC DLL 프로젝트가 전처리기 기호 **\_ USRDLL** 를 정의 하기 때문입니다. MFC 공유 Dll을 사용 하는 DLL은 전처리기 기호 **\_ AFXDLL** 를 정의 하기 때문에 이전 참조에서 AFXDLL 라고도 합니다.

MFC 정적 라이브러리에 연결 하 여 DLL 프로젝트를 만드는 경우 MFC 공유 Dll 없이 DLL을 배포할 수 있습니다. DLL 프로젝트가 가져오기 라이브러리 MFC *버전* 에 연결 되는 경우 LIB 또는 MFC *버전* 의 .lib 인 경우 일치 하는 MFC 공유 DLL mfc *버전* 을 배포 해야 합니다. Dll 또는 MFC *버전이* Dll과 함께U.DLL. 자세한 내용은 [dll](../build/dlls-in-visual-cpp.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[일반 MFC 항목](general-mfc-topics.md)
