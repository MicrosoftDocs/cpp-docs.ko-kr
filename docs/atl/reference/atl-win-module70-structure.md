---
title: _ATL_WIN_MODULE70 구조체
ms.date: 11/04/2016
f1_keywords:
- _ATL_WIN_MODULE70
- ATL::_ATL_WIN_MODULE70
- ATL._ATL_WIN_MODULE70
helpviewer_keywords:
- _ATL_WIN_MODULE70 structure
- ATL_WIN_MODULE70 structure
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
ms.openlocfilehash: 4f1718c76d21f2e13b36c29db785fe989ff6108e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482522"
---
# <a name="atlwinmodule70-structure"></a>_ATL_WIN_MODULE70 구조체

Atl에서 창 작업 코드에서 사용

## <a name="syntax"></a>구문

```
struct _ATL_WIN_MODULE70 {
    UNIT cbSize;
    CRITICAL_SECTION m_csWindowCreate;
    _AtlCreateWndData* m_pCreateWndList;
    CSimpleArray<ATOM> m_rgWindowClassAtoms;
};
```

## <a name="members"></a>멤버

`cbSize`<br/>
버전 관리에 사용 되는 구조체의 크기입니다.

`m_csWindowCreate`<br/>
등록 코드 창에 대 한 액세스를 serialize 하는 데 사용 합니다. ATL.에서 내부적으로 사용

`m_pCreateWndList`<br/>
해당 개체에 windows를 바인딩하는 데 사용 합니다. ATL.에서 내부적으로 사용

`m_rgWindowClassAtoms`<br/>
종료 시 제대로 등록 되지 않을 수도 있습니다 있도록 창 클래스 등록을 추적 하는 데 사용 합니다. ATL.에서 내부적으로 사용

## <a name="remarks"></a>설명

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module) 의 typedef로 정의 된 `_ATL_WIN_MODULE70`합니다.

## <a name="requirements"></a>요구 사항

**헤더:** atlbase.h

## <a name="see-also"></a>참고 항목

[클래스 및 구조체](../../atl/reference/atl-classes.md)

