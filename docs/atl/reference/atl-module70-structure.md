---
description: '다음에 대 한 자세한 정보: _ATL_MODULE70 구조체'
title: _ATL_MODULE70 구조체
ms.date: 11/04/2016
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
ms.openlocfilehash: 8a3076cebe7cab2bce49f660e8198052af393024
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165357"
---
# <a name="_atl_module70-structure"></a>_ATL_MODULE70 구조체

모든 ATL 모듈에서 사용 하는 데이터를 포함 합니다.

## <a name="syntax"></a>구문

```cpp
struct _ATL_MODULE70 {
    UINT cbSize;
    LONG m_nLockCnt;
    _ATL_TERMFUNC_ELEM* m_pTermFuncs;
    CComCriticalSection m_csStaticDataInitAndTypeInfo;
};
```

## <a name="members"></a>멤버

`cbSize`<br/>
버전 관리에 사용 되는 구조의 크기입니다.

`m_nLockCnt`<br/>
모듈의 활성 상태를 유지 해야 하는 기간을 결정 하는 참조 횟수입니다.

`m_pTermFuncs`<br/>
ATL이 종료 될 때 호출 되도록 등록 된 함수를 추적 합니다.

`m_csStaticDataInitAndTypeInfo`<br/>
다중 스레드 상황에서 내부 데이터에 대 한 액세스를 조정 하는 데 사용 됩니다.

## <a name="remarks"></a>설명

[_ATL_MODULE](atl-typedefs.md#_atl_module) 은의 typedef로 정의 됩니다 `_ATL_MODULE70` .

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="see-also"></a>참고 항목

[클래스 및 구조체](../../atl/reference/atl-classes.md)
