---
description: '자세한 정보: 정적으로 MFC에 연결된 기본 MFC DLL'
title: 정적으로 MFC에 연결된 기본 MFC DLL
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++]
- DLLs [C++], regular
- USRDLLs
- USRDLLs, statically linked to MFC
- statically linked DLLs [C++]
- regular MFC DLLs [C++], statically linked to MFC
ms.assetid: 2eed531c-726a-4b8a-b936-f721dc00a7fa
ms.openlocfilehash: b213be6bf076557fc57a5bcac62cbf9767587bd3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273802"
---
# <a name="regular-mfc-dlls-statically-linked-to-mfc"></a>정적으로 MFC에 연결된 기본 MFC DLL

MFC에 정적으로 연결된 기본 MFC DLL은 MFC를 내부적으로 사용하는 DLL이며, 이 DLL의 내보낸 함수는 MFC 또는 비 MFC 실행 파일에서 호출할 수 있습니다. 이름에서 알 수 있듯 관련 종류의 DLL은 MFC의 정적 연결 라이브러리 버전을 사용하여 빌드됩니다. 함수는 일반적으로 기본 MFC DLL에서 표준 C 인터페이스를 사용하여 내보냅니다. 기본 MFC DLL을 작성, 빌드 및 사용하는 방법의 예제는 샘플 [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap)을 참조하세요.

USRDLL이라는 용어는 Visual C++ 설명서에서 더 이상 사용되지 않습니다. 정적으로 MFC에 연결된 기본 MFC DLL는 이전 USRDLL과 특성이 같습니다.

정적으로 MFC에 연결된 기본 MFC DLL의 특징은 다음과 같습니다.

- 클라이언트 실행 파일은 DLL 사용을 지원하는 모든 언어(C, C, C++, Pascal, Visual Basic 등)로 작성할 수 있으며, MFC 애플리케이션이 아니어도 됩니다.

- DLL은 애플리케이션에서 사용하는 동일한 MFC 정적 연결 라이브러리에 연결할 수 있습니다. DLL을 위한 별도 버전의 정적 연결 라이브러리가 더 이상 없습니다.

- MFC 버전 4.0 이전에는 USRDLL이 정적으로 MFC에 연결된 기본 MFC DLL과 같은 종류의 기능을 제공했습니다. Visual C++ 버전 4.0부터 USRDLL이라는 용어가 사용되지 않습니다.

정적으로 MFC에 연결된 기본 MFC DLL에는 다음과 같은 요구 사항이 있습니다.

- 이 형식의 DLL은 `CWinApp`에서 파생된 클래스를 인스턴스화해야 합니다.

- 이 형식의 DLL은 MFC에서 제공하는 `DllMain`을 사용합니다. 일반 MFC 애플리케이션에서처럼 DLL 관련 초기화 코드는 모두 `InitInstance` 멤버 함수에, 종료 코드는 `ExitInstance`에 저장합니다.

- USRDLL이라는 용어는 사용되지 않지만 컴파일러 명령줄에서 “ **_USRDLL**”을 계속 정의해야 합니다. 이 정의는 MFC 헤더 파일에서 가져오는 선언을 결정합니다.

기본 MFC DLL에는 MFC 애플리케이션과 마찬가지로 `CWinApp` 파생 클래스와 해당 애플리케이션 클래스의 단일 개체가 있어야 합니다. 그러나 DLL의 `CWinApp` 개체는 애플리케이션의 `CWinApp` 개체와 마찬가지로 기본 메시지 펌프를 포함하지 않습니다.

애플리케이션이 기본 메시지 펌프를 소유하므로 `CWinApp::Run` 메커니즘은 DLL에 적용되지 않습니다. DLL이 모덜리스 대화 상자를 열거나 자체의 주 프레임 창이 있으면 애플리케이션의 기본 메시지 펌프는 DLL에서 내보낸 루틴을 호출해야 하고 이 루틴은 DLL 애플리케이션 개체의 `CWinApp::PreTranslateMessage` 멤버 함수를 호출합니다.

이 함수의 예제는 DLLScreenCap 샘플을 참조하세요.

기호는 일반적으로 기본 MFC DLL에서 표준 C 인터페이스를 사용하여 내보냅니다. 기본 MFC DLL에서 내보낸 함수 선언은 다음과 같습니다.

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

기본 MFC DLL 내의 모든 메모리 할당이 DLL 내에 유지되어야 하므로, DLL은 다음 중 어느 것도 호출하는 실행 파일에 전달하거나 실행 파일에서 받지 않아야 합니다.

- MFC 개체에 대한 포인터

- MFC에서 할당한 메모리에 대한 포인터

위의 작업을 수행해야 하거나 호출하는 실행 파일과 DLL 간에 MFC 파생 개체를 전달해야 하는 경우에는 MFC 확장 DLL을 빌드해야 합니다.

C 런타임 라이브러리에서 할당한 메모리에 대한 포인터는 데이터의 복사본을 만드는 경우에만 애플리케이션과 DLL 간에 전달하는 것이 안전합니다. 포인터를 삭제하거나 크기를 조정하거나 메모리 복사본을 만들지 않고 사용해서는 안 됩니다.

또한 정적으로 MFC에 연결된 DLL은 공유 MFC DLL에 동적으로 연결할 수 없습니다. 정적으로 MFC에 연결된 DLL은 다른 DLL과 마찬가지로 애플리케이션에 동적으로 바인딩되며, 애플리케이션이 다른 DLL과 마찬가지로 이 DLL에 연결됩니다.

표준 MFC 정적 연결 라이브러리는 [MFC DLL의 명명 규칙](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)에 설명된 규칙에 따라 이름이 지정됩니다. 그러나 MFC 버전 3.0 이상에서는 연결하려는 MFC 라이브러리의 버전을 링커에 수동으로 지정할 필요가 없습니다. 대신, MFC 헤더 파일에서는 **\_DEBUG** 또는 **_UNICODE** 와 같은 전처리기 정의를 기반으로 연결할 MFC 라이브러리의 올바른 버전을 자동으로 결정합니다. MFC 헤더 파일에 /DEFAULTLIB 지시문을 추가하여 링커가 특정 버전의 MFC 라이브러리에 링크하도록 합니다.

## <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [기본 MFC DLL 초기화](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [DLL의 일부로 MFC 사용](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

- [기본 MFC DLL에서 데이터베이스, OLE 및 소켓 MFC 확장명 DLL 사용](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [MFC DLL 만들기](../mfc/reference/mfc-dll-wizard.md)

- [동적으로 MFC에 링크된 기본 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 확장명 DLL](extension-dlls-overview.md)

## <a name="see-also"></a>참조

[DLL의 종류](kinds-of-dlls.md)
