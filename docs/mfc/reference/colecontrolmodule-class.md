---
description: '자세히 알아보기: COleControlModule 클래스'
title: COleControlModule 클래스
ms.date: 11/04/2016
f1_keywords:
- OleControlModule
helpviewer_keywords:
- OLE control modules [MFC]
- MFC ActiveX controls [MFC], OLE control modules
- COleControlModule class [MFC]
- control modules [MFC]
ms.assetid: 0721724d-d4af-4eda-ad34-5a2b27810dd4
ms.openlocfilehash: f88296b7c0e897f82227343b31ca2f639902256e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227483"
---
# <a name="colecontrolmodule-class"></a>COleControlModule 클래스

OLE 컨트롤 모듈 개체를 파생하는 기본 클래스입니다.

## <a name="syntax"></a>구문

```
class COleControlModule : public CWinApp
```

## <a name="remarks"></a>설명

이 클래스는 컨트롤 모듈을 초기화 하는 멤버 함수를 제공 합니다. Microsoft Foundation 클래스를 사용 하는 각 OLE 컨트롤 모듈은에서 파생 된 개체를 하나만 포함할 수 있습니다 `COleControlModule` . 이 개체는 다른 c + + 전역 개체가 생성 될 때 생성 됩니다. `COleControlModule`전역 수준에서 파생 개체를 선언 합니다.

클래스 사용에 대 한 자세한 내용은 `COleControlModule` [CWinApp](../../mfc/reference/cwinapp-class.md) 클래스 및 [ActiveX 컨트롤](../../mfc/mfc-activex-controls.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWinThread](../../mfc/reference/cwinthread-class.md)

[CWinApp](../../mfc/reference/cwinapp-class.md)

`COleControlModule`

## <a name="requirements"></a>요구 사항

**헤더:** afxctl

## <a name="see-also"></a>참고 항목

[MFC 샘플 TESTHELP](../../overview/visual-cpp-samples.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
