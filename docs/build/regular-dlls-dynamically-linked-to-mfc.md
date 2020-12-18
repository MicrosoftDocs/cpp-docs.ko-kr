---
description: '자세한 정보: 동적으로 MFC에 연결된 기본 MFC DLL'
title: 동적으로 MFC에 연결된 기본 MFC DLL
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- AFX_MANAGE_STATE macro
- DLLs [C++], regular
- shared DLL versions [C++]
- dynamically linked DLLs [C++]
ms.assetid: b4f7ab92-8723-42a5-890e-214f4e29dcd0
ms.openlocfilehash: a16320427d881e2d37dd2afedc0566a759d59b9a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273866"
---
# <a name="regular-mfc-dlls-dynamically-linked-to-mfc"></a>동적으로 MFC에 연결된 기본 MFC DLL

동적으로 MFC에 연결된 기본 MFC DLL은 MFC를 내부적으로 사용하는 DLL이며, 이 DLL의 내보낸 함수는 MFC 또는 비 MFC 실행 파일에서 호출할 수 있습니다. 이름에서 알 수 있듯 해당 종류의 DLL은 MFC의 동적 연결 라이브러리 버전(MFC의 공유 버전)을 사용하여 빌드됩니다. 함수는 일반적으로 기본 MFC DLL에서 표준 C 인터페이스를 사용하여 내보냅니다.

MFC에 동적으로 연결되는 기본 MFC DLL에서 내보낸 모든 함수의 시작 부분에 `AFX_MANAGE_STATE` 매크로를 추가하여 현재 모듈 상태를 DLL의 상태로 설정해야 합니다. 이렇게 하려면 DLL에서 내보낸 함수의 시작 부분에 다음 코드 줄을 추가합니다.

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

동적으로 MFC에 연결된 기본 MFC DLL의 특징은 다음과 같습니다.

- Visual C++ 4.0에서 도입된 새로운 DLL 형식입니다.

- 클라이언트 실행 파일은 DLL 사용을 지원하는 모든 언어(C, C, C++, Pascal, Visual Basic 등)로 작성할 수 있으며, MFC 애플리케이션이 아니어도 됩니다.

- 정적으로 연결된 기본 MFC DLL과 달리 이 형식의 DLL은 MFC DLL(공유 MFC DLL이라고도 함)에 동적으로 연결됩니다.

- 이 형식의 DLL에 연결된 MFC 가져오기 라이브러리는 MFC DLL을 사용하는 애플리케이션 또는 MFC 확장 DLL에 사용되는 것과 같은 MFCxx(D).lib입니다.

동적으로 MFC에 연결된 기본 MFC DLL에는 다음과 같은 요구 사항이 있습니다.

- 해당 DLL은 MFC DLL에 동적으로 연결되는 실행 파일과 마찬가지로 **_AFXDLL** 을 정의하여 컴파일됩니다. 그러나 정적으로 MFC에 연결된 기본 MFC DLL과 마찬가지로 **_USRDLL** 도 정의됩니다.

- 이 형식의 DLL은 `CWinApp` 파생 클래스를 인스턴스화해야 합니다.

- 이 형식의 DLL은 MFC에서 제공하는 `DllMain`을 사용합니다. 일반 MFC 애플리케이션에서처럼 DLL 관련 초기화 코드는 모두 `InitInstance` 멤버 함수에, 종료 코드는 `ExitInstance`에 저장합니다.

해당 종류의 DLL은 MFC의 동적 연결 라이브러리 버전을 사용하므로 현재 모듈 상태를 DLL의 상태로 명시적으로 설정해야 합니다. 이렇게 하려면 DLL에서 내보낸 모든 함수의 시작 부분에 [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) 매크로를 사용합니다.

기본 MFC DLL에는 MFC 애플리케이션과 마찬가지로 `CWinApp` 파생 클래스와 해당 애플리케이션 클래스의 단일 개체가 있어야 합니다. 그러나 DLL의 `CWinApp` 개체는 애플리케이션의 `CWinApp` 개체와 마찬가지로 기본 메시지 펌프를 포함하지 않습니다.

애플리케이션이 기본 메시지 펌프를 소유하므로 `CWinApp::Run` 메커니즘은 DLL에 적용되지 않습니다. DLL이 모덜리스 대화 상자를 표시하거나 자체의 주 프레임 창이 있는 경우 애플리케이션의 기본 메시지 펌프는 `CWinApp::PreTranslateMessage`를 호출하는 DLL에서 내보낸 루틴을 호출해야 합니다.

일반 MFC 애플리케이션에서처럼 DLL 관련 초기화를 모두 `CWinApp::InitInstance` 멤버 함수에 저장합니다. `CWinApp` 파생 클래스의 `CWinApp::ExitInstance` 멤버 함수는 DLL을 언로드하기 전에 MFC가 제공한 `DllMain` 함수에서 호출됩니다.

공유 DLL MFCx0.dll 및 Msvcr*0.dll(또는 유사한 파일)을 애플리케이션에 배포해야 합니다.

MFC에 동적으로 연결된 DLL을 MFC에 정적으로도 연결할 수는 없습니다. 애플리케이션은 다른 DLL과 마찬가지로 MFC에 동적으로 연결된 기본 MFC DLL에 연결됩니다.

기호는 일반적으로 기본 MFC DLL에서 표준 C 인터페이스를 사용하여 내보냅니다. 기본 MFC DLL에서 내보낸 함수 선언은 다음과 같습니다.

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

기본 MFC DLL 내의 모든 메모리 할당이 DLL 내에 유지되어야 하므로, DLL은 다음 중 어느 것도 호출하는 실행 파일에 전달하거나 실행 파일에서 받지 않아야 합니다.

- MFC 개체에 대한 포인터

- MFC에서 할당한 메모리에 대한 포인터

위의 작업을 수행해야 하거나 호출하는 실행 파일과 DLL 간에 MFC 파생 개체를 전달해야 하는 경우에는 MFC 확장 DLL을 빌드해야 합니다.

C 런타임 라이브러리에서 할당한 메모리에 대한 포인터는 데이터의 복사본을 만드는 경우에만 애플리케이션과 DLL 간에 전달하는 것이 안전합니다. 포인터를 삭제하거나 크기를 조정하거나 메모리 복사본을 만들지 않고 사용해서는 안 됩니다.

MFC에 동적으로 연결되는 기본 MFC DLL을 빌드하는 경우 [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) 매크로를 사용하여 MFC 모듈 상태를 올바로 전환해야 합니다. 이렇게 하려면 DLL에서 내보낸 함수의 시작 부분에 다음 코드 줄을 추가합니다.

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

MFC에 정적으로 연결되는 기본 MFC DLL 또는 MFC 확장 DLL에서는 **AFX_MANAGE_STATE** 매크로를 사용할 수 없습니다. 자세한 내용은 [MFC 모듈의 상태 데이터 관리](../mfc/managing-the-state-data-of-mfc-modules.md)를 참조하세요.

기본 MFC DLL을 작성, 빌드 및 사용하는 방법의 예제는 샘플 [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap)을 참조하세요. MFC에 동적으로 연결되는 기본 MFC DLL에 대한 자세한 내용은 샘플의 요약에서 “MFC DLL에 동적으로 연결하도록 DLLScreenCap 변환” 섹션을 참조하세요.

## <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [기본 MFC DLL 초기화](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [동적으로 MFC에 연결된 기본 MFC DLL의 모듈 상태](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)

- [MFC 모듈의 상태 데이터 관리](../mfc/managing-the-state-data-of-mfc-modules.md)

- [기본 MFC DLL에서 데이터베이스, OLE 및 소켓 MFC 확장명 DLL 사용](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [DLL의 일부로 MFC 사용](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

## <a name="see-also"></a>참조

[DLL의 종류](kinds-of-dlls.md)
