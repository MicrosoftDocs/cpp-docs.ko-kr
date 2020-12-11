---
description: '자세한 정보: COM 인터페이스 진입점'
title: COM 인터페이스 진입점
ms.date: 03/27/2019
helpviewer_keywords:
- entry points, COM interfaces
- state management, OLE/COM interfaces
- MFC COM, COM interface entry points
- OLE, interface entry points
- MFC, managing state data
- COM interfaces, entry points
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
ms.openlocfilehash: 805ac906c3ccca246d1af71c689aaf768f789999
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160014"
---
# <a name="com-interface-entry-points"></a>COM 인터페이스 진입점

COM 인터페이스의 멤버 함수에 대해, 매크로를 사용 `METHOD_PROLOGUE` 하 여 내보낸 인터페이스의 메서드를 호출할 때 적절 한 전역 상태를 유지 합니다.

일반적으로 파생 개체에서 구현 하는 인터페이스의 멤버 함수는 `CCmdTarget` 이미이 매크로를 사용 하 여 포인터의 자동 초기화를 제공 `pThis` 합니다. 예를 들어:

[!code-cpp[NVC_MFCConnectionPoints#5](codesnippet/cpp/com-interface-entry-points_1.cpp)]

자세한 내용은 MFC/OLE 구현에서 [기술 정보 38](tn038-mfc-ole-iunknown-implementation.md) 을 참조 하세요 `IUnknown` .

`METHOD_PROLOGUE`매크로는 다음과 같이 정의 됩니다.

```cpp
#define METHOD_PROLOGUE(theClass, localClass) \
    theClass* pThis = \
    ((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \
    AFX_MANAGE_STATE(pThis->m_pModuleState) \
```

전역 상태를 관리 하는 것과 관련 된 매크로 부분은 다음과 같습니다.

`AFX_MANAGE_STATE( pThis->m_pModuleState )`

이 식에서 *m_pModuleState* 는 포함 하는 개체의 멤버 변수로 간주 됩니다. 이 클래스는 기본 클래스에 의해 구현 되며 `CCmdTarget` `COleObjectFactory` , 개체가 인스턴스화될 때에서 적절 한 값으로 초기화 됩니다.

## <a name="see-also"></a>참고 항목

[MFC 모듈의 상태 데이터 관리](managing-the-state-data-of-mfc-modules.md)
