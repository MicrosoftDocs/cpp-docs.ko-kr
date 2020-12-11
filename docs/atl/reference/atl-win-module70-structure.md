---
description: '다음에 대 한 자세한 정보: _ATL_WIN_MODULE70 구조체'
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
ms.openlocfilehash: 11b7fdad71fa8c7b615a0e6873571c38420c9b5d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158623"
---
# <a name="_atl_win_module70-structure"></a>_ATL_WIN_MODULE70 구조체

ATL의 창 고 코드에서 사용 됩니다.

## <a name="syntax"></a>구문

```cpp
struct _ATL_WIN_MODULE70 {
    UNIT cbSize;
    CRITICAL_SECTION m_csWindowCreate;
    _AtlCreateWndData* m_pCreateWndList;
    CSimpleArray<ATOM> m_rgWindowClassAtoms;
};
```

## <a name="members"></a>멤버

`cbSize`<br/>
버전 관리에 사용 되는 구조의 크기입니다.

`m_csWindowCreate`<br/>
창 등록 코드에 대 한 액세스를 serialize 하는 데 사용 됩니다. ATL에서 내부적으로 사용 됩니다.

`m_pCreateWndList`<br/>
창을 해당 개체에 바인딩하는 데 사용 됩니다. ATL에서 내부적으로 사용 됩니다.

`m_rgWindowClassAtoms`<br/>
종료 시 적절히 등록 취소할 수 있도록 창 클래스 등록을 추적 하는 데 사용 됩니다. ATL에서 내부적으로 사용 됩니다.

## <a name="remarks"></a>설명

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module) 은의 typedef로 정의 됩니다 `_ATL_WIN_MODULE70` .

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="see-also"></a>참고 항목

[클래스 및 구조체](../../atl/reference/atl-classes.md)
