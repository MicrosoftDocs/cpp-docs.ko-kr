---
description: 'TN011: DLL의 일부로 MFC 사용에 대해 자세히 알아보세요.'
title: 'TN011: DLL의 일부로 MFC 사용'
ms.date: 11/04/2016
helpviewer_keywords:
- _USRDLL symbol
- USRDLLs, compiler switches
- TN011
- DLLs [MFC], linking
- MFC DLLs [MFC], linking regular MFC DLLs to MFC
ms.assetid: 76753e9c-59dc-40f6-b6a7-f6bb9a7c4190
ms.openlocfilehash: 11b50ce361fc9e41c48931daa6bffd30a8c9673e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216030"
---
# <a name="tn011-using-mfc-as-part-of-a-dll"></a>TN011: DLL의 일부로 MFC 사용

이 참고는 MFC 라이브러리를 Windows DLL (동적 연결 라이브러리)의 일부로 사용할 수 있도록 하는 일반적인 MFC Dll에 대해 설명 합니다. 사용자가 Windows Dll 및 빌드하는 방법에 대해 잘 알고 있다고 가정 합니다. Mfc 라이브러리에 대 한 확장을 만들 수 있는 MFC 확장명 Dll에 대 한 자세한 내용은 [mfc의 DLL 버전](../mfc/tn033-dll-version-of-mfc.md)을 참조 하세요.

## <a name="dll-interfaces"></a>DLL 인터페이스

일반 MFC Dll은 응용 프로그램과 DLL 간의 인터페이스가 C와 같은 함수 또는 명시적으로 내보낸 클래스에 지정 되어 있다고 가정 합니다. MFC 클래스 인터페이스를 내보낼 수 없습니다.

DLL과 응용 프로그램 모두에서 MFC를 사용 하려는 경우에는 둘 다 MFC 라이브러리의 공유 버전을 사용 하거나 라이브러리의 복사본에 정적으로 연결할 수 있습니다. 응용 프로그램과 DLL은 모두 표준 버전의 MFC 라이브러리 중 하나를 사용할 수 있습니다.

기본 MFC Dll에는 다음과 같은 여러 가지 이점이 있습니다.

- DLL을 사용 하는 응용 프로그램은 MFC를 사용할 필요가 없으며 Visual C++ 응용 프로그램 일 필요가 없습니다.

- 정적으로 MFC에 링크 하는 일반 MFC Dll을 사용 하는 경우 DLL의 크기는 사용 및 연결 된 MFC 및 C 런타임 루틴에만 의존 합니다.

- MFC에 동적으로 연결 되는 일반 MFC Dll을 사용 하면 공유 버전의 MFC를 사용 하 여 메모리를 절약 하는 것이 중요할 수 있습니다. 그러나 DLL을 사용 하 여 공유 Dll, Mfc \<*version*> .dll 및 Msvvcrt를 배포 해야 합니다 \<*version*> .

- DLL 디자인은 클래스가 구현 되는 방식과 무관 합니다. DLL 디자인은 원하는 Api로만 내보냅니다. 결과적으로 구현이 변경 되 면 일반 MFC Dll이 여전히 유효 합니다.

- 정적으로 MFC에 링크 하는 일반 MFC Dll을 사용 하는 경우 DLL과 응용 프로그램 모두에서 MFC를 사용 하는 경우 DLL과 다른 버전의 MFC를 필요로 하는 응용 프로그램에 문제가 발생 하지 않으며 그 반대의 경우도 마찬가지입니다. MFC 라이브러리는 각 DLL 또는 EXE에 정적으로 연결 되므로 사용자가 보유 한 버전에 대해 질문이 없습니다.

## <a name="api-limitations"></a>API 제한 사항

일부 MFC 기능은 기술 제한 사항으로 인해 또는 이러한 서비스가 응용 프로그램에서 일반적으로 제공 되기 때문에 DLL 버전에 적용 되지 않습니다. 현재 버전의 MFC를 사용 하는 경우에만 적용 되는 유일한 함수는 `CWinApp::SetDialogBkColor` 입니다.

## <a name="building-your-dll"></a>DLL 빌드

정적으로 MFC에 링크 하는 일반 MFC Dll을 컴파일하는 경우에는 기호와 기호가 정의 되어야 합니다 `_USRDLL` `_WINDLL` . 다음 컴파일러 스위치를 사용 하 여 DLL 코드도 컴파일해야 합니다.

- **/D_WINDLL** DLL에 대 한 컴파일을 나타냅니다.

- **/D_USRDLL** 일반 MFC DLL을 빌드 하도록 지정 합니다.

또한 이러한 기호를 정의 하 고 동적으로 MFC에 링크 하는 일반 MFC Dll을 컴파일할 때 이러한 컴파일러 스위치를 사용 해야 합니다. 또한 기호가 정의 되어야 `_AFXDLL` 하며 DLL 코드를로 컴파일해야 합니다.

- **/D_AFXDLL** 동적으로 mfc에 링크 하는 일반 mfc DLL을 빌드 하도록 지정 합니다.

응용 프로그램과 DLL 사이의 인터페이스 (Api)는 명시적으로 내보내야 합니다. 인터페이스를 낮은 대역폭으로 정의 하 고 가능 하면 C 인터페이스만 사용 하는 것이 좋습니다. 직접 C 인터페이스는 보다 복잡 한 c + + 클래스 보다 유지 관리가 쉽습니다.

C 및 c + + 파일에 포함 될 수 있는 별도의 헤더에 Api를 넣습니다. 예제는 MFC 고급 개념 샘플 [DLLScreenCap](../overview/visual-cpp-samples.md) 에서 헤더 ScreenCap. h를 참조 하세요. 함수를 내보내려면 `EXPORTS` 모듈 정의 파일 ()의 섹션에 함수를 입력 합니다. DEF)로 `__declspec(dllexport)` 설정 하거나 함수 정의에을 포함 합니다. `__declspec(dllimport)`를 사용 하 여 이러한 함수를 클라이언트 실행 파일로 가져옵니다.

MFC에 동적으로 연결 되는 일반 MFC Dll에서 내보낸 모든 함수의 시작 부분에 AFX_MANAGE_STATE 매크로를 추가 해야 합니다. 이 매크로는 현재 모듈 상태를 DLL에 대 한 상태로 설정 합니다. 이 매크로를 사용 하려면 DLL에서 내보낸 함수의 시작 부분에 다음 코드 줄을 추가 합니다.

`AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`

## <a name="winmain---dllmain"></a>WinMain-> DllMain

MFC 라이브러리는 `DllMain` 일반적인 mfc 응용 프로그램에서와 같이 [CWinApp](../mfc/reference/cwinapp-class.md) 파생 개체를 초기화 하는 표준 Win32 진입점을 정의 합니다. 모든 DLL 관련 초기화를 일반적인 MFC 응용 프로그램과 마찬가지로 [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) 메서드에 넣습니다.

응용 프로그램이 주 메시지 펌프를 소유 하기 때문에 [CWinApp:: Run](../mfc/reference/cwinapp-class.md#run) 메커니즘은 DLL에 적용 되지 않습니다. DLL이 모덜리스 대화 상자를 표시 하거나 주 프레임 창이 있는 경우 응용 프로그램의 기본 메시지 펌프는 [CWinApp::P retranslatemessage](../mfc/reference/cwinapp-class.md#pretranslatemessage)를 호출 하는 DLL로 내보낸 루틴을 호출 해야 합니다.

이 함수를 사용 하는 DLLScreenCap 샘플을 참조 하세요.

`DllMain`MFC에서 제공 하는 함수는 DLL이 언로드되기 전에에서 파생 된 클래스의 [CWinApp:: exitinstance](../mfc/reference/cwinapp-class.md#exitinstance) 메서드를 호출 합니다 `CWinApp` .

## <a name="linking-your-dll"></a>DLL 연결

정적으로 MFC에 링크 하는 일반적인 MFC Dll을 사용 하 여 DLL을 Nafxcwd.lib 또는 Nafxcw와 Libcmt.lib 이라는 C 런타임 버전에 연결 해야 합니다. 이러한 라이브러리는 미리 작성 되었으며 Visual C++ 설치 프로그램을 실행할 때 지정 하 여 설치할 수 있습니다.

## <a name="sample-code"></a>샘플 코드

전체 샘플은 MFC 고급 개념 샘플 프로그램 DLLScreenCap을 참조 하세요. 이 샘플에서 주목할 만한 몇 가지 사항은 다음과 같습니다.

- DLL의 컴파일러 플래그와 응용 프로그램의 플래그는 다릅니다.

- 링크 줄 및입니다. DLL 및 응용 프로그램에 대 한 DEF 파일이 다릅니다.

- DLL을 사용 하는 응용 프로그램은 c + + 일 필요가 없습니다.

- 응용 프로그램과 DLL 사이의 인터페이스는 C 또는 c + +에서 사용할 수 있는 API 이며 DLLScreenCap를 사용 하 여 내보내집니다.

다음 예제에서는 정적으로 MFC에 링크 하는 일반 MFC DLL에 정의 된 API를 보여 줍니다. 이 예제에서 선언은 `extern "C" { }` c + + 사용자에 대 한 블록으로 묶여 있습니다. 여기에는 여러 가지 이점이 있습니다. 먼저 C + + 이외의 클라이언트 응용 프로그램에서 DLL Api를 사용할 수 있도록 합니다. 두 번째로 내보낸 이름에는 c + + 이름 적용이 적용 되지 않기 때문에 DLL 오버 헤드가 줄어듭니다. 마지막으로에 명시적으로 추가 하는 것이 더 쉽습니다. 이름 사용에 대해 걱정할 필요 없이 .DEF 파일 (서 수로 내보내기)

```cpp
#ifdef __cplusplus
extern "C" {
#endif  /* __cplusplus */

struct TracerData
{
    BOOL bEnabled;
    UINT flags;
};

BOOL PromptTraceFlags(TracerData FAR* lpData);

#ifdef __cplusplus
}
#endif
```

API에서 사용 하는 구조체는 MFC 클래스에서 파생 되지 않으며 API 헤더에 정의 됩니다. 이렇게 하면 DLL과 응용 프로그램 간의 인터페이스 복잡성이 줄어들고 C 프로그램에서 DLL을 사용할 수 있게 됩니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
