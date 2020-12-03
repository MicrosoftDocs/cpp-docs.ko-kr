---
title: 기본 MFC DLL에서 데이터베이스, OLE 및 소켓 MFC 확장 DLL 사용
description: 기본 MFC DLL에서 데이터베이스, OLE 및 소켓 MFC 확장 DLL을 사용하는 방법을 설명합니다.
ms.date: 11/30/2020
helpviewer_keywords:
- DLLs [C++], initializing
- DLLs [C++], extension
- DLLs [C++], regular
ms.openlocfilehash: a28e80c4d554a86f45f708e661382ee4a54eca9e
ms.sourcegitcommit: 432c24dde31c400437c4320e8432b1ddb232f844
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440278"
---
# <a name="using-database-ole-and-sockets-mfc-extension-dlls-in-regular-mfc-dlls"></a>기본 MFC DLL에서 데이터베이스, OLE 및 소켓 MFC 확장 DLL 사용

기본 MFC DLL에서 MFC 확장 DLL을 사용하는 경우 MFC 확장 DLL이 기본 MFC DLL의 `CDynLinkLibrary` 개체 체인에 연결되어 있지 않으면 관련 문제가 하나 이상 발생할 수 있습니다. MFC 데이터베이스, OLE 및 소켓 지원 DLL의 디버그 버전은 MFC 확장 DLL로 구현되므로 고유한 MFC 확장 DLL을 명시적으로 사용하지 않더라도 해당 MFC 기능을 사용하는 경우 유사한 문제가 나타날 수 있습니다. 몇 가지 증상은 다음과 같습니다.

- MFC 확장 DLL에 정의된 클래스 형식의 개체를 역직렬화하려고 하면 “경고: 보관에서 CYourClass를 로드할 수 없습니다. 정의되지 않은 클래스입니다.” 메시지가 추적 디버그 창에 표시되고 개체가 직렬화되지 않습니다.

- 잘못된 클래스를 나타내는 예외가 throw될 수 있습니다.

- `AfxFindResourceHandle`이 `NULL` 또는 잘못된 리소스 핸들을 반환하므로 MFC 확장 DLL에 저장된 리소스가 로드되지 않습니다.

- `DllGetClassObject`와 `DllCanUnloadNow`, 그리고 `COleObjectFactory`의 `UpdateRegistry`, `Revoke`, `RevokeAll` 및 `RegisterAll` 멤버 함수가 MFC 확장 DLL에 정의된 클래스 팩터리를 찾지 못합니다.

- `AfxDoForAllClasses`가 MFC 확장 DLL의 모든 클래스에서 작동하지 않습니다.

- 표준 MFC 데이터베이스, 소켓 또는 OLE 리소스가 로드되지 않습니다. 예를 들어 기본 MFC DLL에서 MFC 데이터베이스 클래스를 올바로 사용하는 경우에도 `AfxLoadString(AFX_IDP_SQL_CONNECT_FAIL)`에서 빈 문자열을 반환합니다.

관련 문제의 솔루션은 `CDynLinkLibrary` 개체를 만드는 MFC 확장 DLL에서 초기화 함수를 만들고 내보내는 것입니다. MFC 확장 DLL을 사용하는 각 기본 MFC DLL에서 이 초기화 함수를 정확히 한 번 호출합니다.

## <a name="mfc-ole-mfc-database-or-dao-or-mfc-sockets-support"></a>MFC OLE, MFC 데이터베이스(또는 DAO) 또는 MFC 소켓 지원

기본 MFC DLL에서 MFC OLE, MFC 데이터베이스(또는 DAO) 또는 MFC 소켓 지원을 사용하는 경우 MFC 디버그 MFC 확장 *`MFCOxxD.dll`* , *`MFCDxxD.dll`* , *`MFCNxxD.dll`* (여기서 *xx* 는 버전 번호)이 각각 자동으로 연결됩니다. 사용하는 각 DLL에 대해 미리 정의된 초기화 함수를 호출합니다.

- 데이터베이스를 지원하려면 기본 MFC DLL의 `CWinApp::InitInstance` 함수에 `AfxDbInitModule` 호출을 추가합니다. 이 호출은 *`MFCDxxD.dll`* 에 액세스하는 모든 기본 클래스 호출 또는 추가 코드 전에 수행되어야 합니다. 이 함수는 매개 변수를 사용하지 않으며 `void`를 반환합니다.

- OLE를 지원하려면 기본 MFC DLL의 `CWinApp::InitInstance` 함수에 `AfxOleInitModule` 호출을 추가합니다. `COleControlModule::InitInstance` 함수는 이미 `AfxOleInitModule`을 호출하므로 OLE 컨트롤을 빌드하고 `COleControlModule`을 사용하는 경우 이 호출을 `AfxOleInitModule`에 추가하면 안 됩니다.

- 소켓을 지원하려면 기본 MFC DLL의 `CWinApp::InitInstance`에 `AfxNetInitModule` 호출을 추가합니다.

MFC DLL 및 애플리케이션의 릴리스 빌드에서는 데이터베이스, 소켓 또는 OLE 지원을 위해 별도의 DLL을 사용하지 않습니다. 그러나 릴리스 모드에서 초기화 함수를 호출하는 것이 안전합니다.

## <a name="cdynlinklibrary-objects"></a>CDynLinkLibrary 개체

이 문서의 시작 부분에서 언급한 각 작업 중에 MFC는 특정한 값이나 개체를 검색해야 합니다. 예를 들어 deserialization 중에 MFC는 현재 사용 가능한 모든 런타임 클래스를 검색하여 보관의 개체를 해당하는 적절한 런타임 클래스와 일치시켜야 합니다.

검색의 일부로 MFC는 `CDynLinkLibrary` 개체 체인을 검색하여 사용 중인 모든 MFC 확장 DLL을 검사합니다. `CDynLinkLibrary` 개체는 생성 중 체인에 자동으로 연결되며, 초기화 중 각 MFC 확장 DLL에 의해 차례로 만들어집니다. 모든 모듈(애플리케이션 또는 기본 MFC DLL)에는 고유한 `CDynLinkLibrary` 개체 체인이 있습니다.

MFC 확장 DLL이 `CDynLinkLibrary` 체인에 연결되려면 MFC 확장 DLL을 사용하는 모든 모듈의 컨텍스트에서 `CDynLinkLibrary` 개체를 만들어야 합니다. 기본 MFC DLL에서 MFC 확장 DLL을 사용하려는 경우 확장 DLL이 `CDynLinkLibrary` 개체를 만드는 내보낸 초기화 함수를 제공해야 합니다. MFC 확장 DLL을 사용하는 모든 기본 MFC DLL은 내보낸 초기화 함수를 호출해야 합니다.

MFC 확장 DLL을 MFC 애플리케이션에서만 사용하고 기본 MFC DLL에서는 사용하지 않는 경우에는 MFC 확장 DLL의 `DllMain` 함수에서 `CDynLinkLibrary` 개체를 만들면 됩니다. 이 작업은 MFC DLL 마법사 MFC 확장 DLL 코드에서 수행합니다. MFC 확장 DLL을 암시적으로 로드하면 애플리케이션이 시작하기 전에 `DllMain`이 로드되고 실행됩니다. 모든 `CDynLinkLibrary` 만들기는 MFC DLL이 MFC 애플리케이션을 위해 예약하는 기본 체인에 연결됩니다.

하나의 MFC 확장 DLL에서 하나의 체인에 여러 `CDynLinkLibrary` 개체를 포함하는 것은 좋지 않습니다. MFC 확장 DLL을 메모리에서 동적으로 언로드할 수 있는 경우에는 특히 그렇습니다. 하나의 모듈에서 초기화 함수를 두 번 이상 호출하지 마세요.

## <a name="sample-code"></a>샘플 코드

이 샘플 코드에서는 기본 MFC DLL을 MFC 확장 DLL에 암시적으로 연결한다고 가정합니다. 암시적으로 연결하려면 기본 MFC DLL을 빌드할 때 MFC 확장 DLL의 가져오기 라이브러리(LIB 파일)에 연결합니다.

MFC 확장 DLL의 소스에 다음 줄이 있어야 합니다.

```cpp
// YourExtDLL.cpp:

// standard MFC extension DLL routines
#include "afxdllx.h"

static AFX_EXTENSION_MODULE extensionDLL;

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    if (dwReason == DLL_PROCESS_ATTACH)
    {
        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(extensionDLL, hInstance))
           return 0;
    }
    return 1;   // ok
}

// Exported DLL initialization is run in context of
// application or regular MFC DLL
extern "C" void WINAPI InitYourExtDLL()
{
    // create a new CDynLinkLibrary for this app
    new CDynLinkLibrary(extensionDLL);

    // add other initialization here
}
```

**InitYourExtDLL** 함수를 내보내야 합니다. **`__declspec(dllexport)`** 을 사용하거나 다음과 같이 DLL의 DEF 파일에 내보낼 수 있습니다.

```def
// YourExtDLL.Def:
LIBRARY      YOUREXTDLL
CODE         PRELOAD MOVEABLE DISCARDABLE
DATA         PRELOAD SINGLE
EXPORTS
    InitYourExtDLL
```

MFC 확장 DLL을 사용하는 각 기본 MFC DLL에서 `CWinApp` 파생 개체의 `InitInstance` 멤버 호출을 추가합니다.

```cpp
// YourRegularDLL.cpp:

class CYourRegularDLL : public CWinApp
{
public:
    virtual BOOL InitInstance(); // Initialization
    virtual int ExitInstance();  // Termination

    // nothing special for the constructor
    CYourRegularDLL(LPCTSTR pszAppName) : CWinApp(pszAppName) { }
};

BOOL CYourRegularDLL::InitInstance()
{
    // any DLL initialization goes here
    TRACE0("YOUR regular MFC DLL initializing\n");

    // wire any MFC extension DLLs into CDynLinkLibrary chain
    InitYourExtDLL();

    return TRUE;
}
```

### <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [MFC 확장 DLL 초기화](run-time-library-behavior.md#initializing-extension-dlls)

- [기본 MFC DLL 초기화](run-time-library-behavior.md#initializing-regular-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [MFC 확장명 DLL](extension-dlls.md)

- [정적으로 MFC에 링크된 기본 MFC DLL](regular-dlls-statically-linked-to-mfc.md)

- [동적으로 MFC에 링크된 기본 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [DLL의 일부로 MFC 사용](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [MFC의 DLL 버전](../mfc/tn033-dll-version-of-mfc.md)

## <a name="see-also"></a>참조

[MFC 확장명 DLL](extension-dlls.md)
