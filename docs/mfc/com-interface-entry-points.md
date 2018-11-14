---
title: COM 인터페이스 진입점
ms.date: 11/04/2016
helpviewer_keywords:
- entry points, COM interfaces
- state management, OLE/COM interfaces
- MFC COM, COM interface entry points
- OLE, interface entry points
- MFC, managing state data
- COM interfaces, entry points
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
ms.openlocfilehash: 0a8db9c6920b4223296f700d084e0b59b9b3ef15
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521221"
---
# <a name="com-interface-entry-points"></a>COM 인터페이스 진입점

COM 인터페이스의 멤버 함수를 사용 합니다 [METHOD_PROLOGUE](com-interface-entry-points.md#method_prologue) 내보낸된 인터페이스의 메서드를 호출할 때 적절 한 전역 상태를 유지 하는 매크로입니다.

인터페이스의 멤버 함수에서 구현 되는 일반적으로 `CCmdTarget`-파생된 개체의 자동 초기화를 제공 하려면이 매크로 이미 사용 된 `pThis` 포인터입니다. 예를 들어:

[!code-cpp[NVC_MFCConnectionPoints#5](../mfc/codesnippet/cpp/com-interface-entry-points_1.cpp)]

자세한 내용은 참조 하세요. [기술 참고 38](../mfc/tn038-mfc-ole-iunknown-implementation.md) MFC/OLE에 `IUnknown` 구현 합니다.

`METHOD_PROLOGUE` 매크로로 정의 됩니다.

```cpp
#define METHOD_PROLOGUE(theClass, localClass) \
    theClass* pThis = \
    ((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \
    AFX_MANAGE_STATE(pThis->m_pModuleState) \
```

전역 상태 관리와 관련된 매크로 부분은 다음과 같습니다.

`AFX_MANAGE_STATE( pThis->m_pModuleState )`

이 식에서 *m_pModuleState* 포함 하는 개체의 멤버 변수 것으로 간주 됩니다. 에 의해 구현 됩니다 합니다 `CCmdTarget` 기본 클래스 및 적절 한 값으로 초기화 됩니다 `COleObjectFactory`개체를 인스턴스화할 때, 합니다.

## <a name="see-also"></a>참고 항목

[MFC 모듈의 상태 데이터 관리](../mfc/managing-the-state-data-of-mfc-modules.md)

