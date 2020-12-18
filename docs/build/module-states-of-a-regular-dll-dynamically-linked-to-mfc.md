---
description: '자세한 정보: 동적으로 MFC에 연결된 기본 MFC DLL의 모듈 상태'
title: 동적으로 MFC에 연결된 기본 MFC DLL의 모듈 상태
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- module states [C++]
- MFC DLLs [C++], regular MFC DLLs
- module states [C++], regular MFC DLLs dynamically linked to
- DLLs [C++], module states
ms.assetid: b4493e79-d25e-4b7f-a565-60de5b32c723
ms.openlocfilehash: 4cf1720e7aff21f13b7486517e626307ef6731a6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187509"
---
# <a name="module-states-of-a-regular-mfc-dll-dynamically-linked-to-mfc"></a>동적으로 MFC에 연결된 기본 MFC DLL의 모듈 상태

기본 MFC DLL을 MFC DLL에 동적으로 연결하는 기능을 사용하면 매우 복잡한 몇 가지 구성을 사용할 수 있습니다. 예를 들어 기본 MFC DLL과 이 DLL을 사용하는 실행 파일이 모두 MFC DLL 및 원하는 MFC 확장 DLL에 동적으로 연결할 수 있습니다.

이 구성에서는 현재 `CWinApp` 개체 및 핸들 맵에 대한 포인터와 같은 MFC 글로벌 데이터와 관련된 문제가 발생합니다.

MFC 버전 4.0 이전에는 이 글로벌 데이터가 MFC DLL 자체에 있었고 프로세스의 모든 모듈에서 공유되었습니다. Win32 DLL을 사용하는 각 프로세스가 자체의 DLL 데이터 복사본을 가져오므로 이 체계에서는 프로세스별 데이터를 쉽게 추적하는 방법을 제공했습니다. 또한 AFXDLL 모델에서는 프로세스에 `CWinApp` 개체 하나와 한 세트의 핸들 맵만 있다고 가정했으므로 MFC DLL 자체에서 관련 항목을 추적할 수 있었습니다.

그러나 기본 MFC DLL을 MFC DLL에 동적으로 연결하는 기능을 사용하면 프로세스에 둘 이상의 `CWinApp` 개체가 있을 수 있고 핸들 맵도 두 세트 이상 있을 수 있습니다. MFC에서 사용해야 하는 항목을 추적하는 방법은 무엇인가요?

솔루션은 각 모듈(애플리케이션 또는 기본 MFC DLL)에 이 전역 상태 정보의 고유한 복사본을 제공하는 것입니다. 따라서 기본 MFC DLL에서 **AfxGetApp** 호출하면 실행 파일이 아닌 DLL에 있는 `CWinApp` 개체의 포인터가 반환됩니다. MFC 글로벌 데이터의 이 모듈별 복사본은 모듈 상태라고 하며 [MFC 기술 참고 58](../mfc/tn058-mfc-module-state-implementation.md)에 설명되어 있습니다.

MFC 공용 창 프로시저는 올바른 모듈 상태로 자동 전환되므로 기본 MFC DLL에서 구현되는 메시지 처리기에서는 걱정할 필요가 없습니다. 그러나 실행 파일이 기본 MFC DLL로 호출되는 경우에는 현재 모듈 상태를 DLL의 상태로 명시적으로 설정해야 합니다. 이렇게 하려면 DLL에서 내보낸 모든 함수에서 **AFX_MANAGE_STATE** 매크로를 사용합니다. 이렇게 하려면 DLL에서 내보낸 함수의 시작 부분에 다음 코드 줄을 추가합니다.

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [MFC 모듈의 상태 데이터 관리](../mfc/managing-the-state-data-of-mfc-modules.md)

- [동적으로 MFC에 연결된 기본 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 확장명 DLL](extension-dlls-overview.md)

## <a name="see-also"></a>참조

[Visual Studio에서 C/C++ DLL 만들기](dlls-in-visual-cpp.md)
