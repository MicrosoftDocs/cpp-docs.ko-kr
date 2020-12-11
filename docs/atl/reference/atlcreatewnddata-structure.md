---
description: '다음에 대 한 자세한 정보: _AtlCreateWndData 구조체'
title: _AtlCreateWndData 구조체
ms.date: 11/04/2016
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
ms.openlocfilehash: 912f2d108baa9cae1b91a34f3c5e386339d11f0b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158610"
---
# <a name="_atlcreatewnddata-structure"></a>_AtlCreateWndData 구조체

이 구조에는 ATL의 창 고 코드에 클래스 인스턴스 데이터가 포함 됩니다.

## <a name="syntax"></a>구문

```cpp
    struct _AtlCreateWndData{
    void* m_pThis;
    DWORD m_dwThreadID;
    _AtlCreateWndData* m_pNext;
};
```

## <a name="members"></a>멤버

`m_pThis`<br/>
**`this`** 창 프로시저의 클래스 인스턴스에 대 한 액세스 권한을 얻는 데 사용 되는 포인터입니다.

`m_dwThreadID`<br/>
현재 클래스 인스턴스의 스레드 ID입니다.

`m_pNext`<br/>
다음 개체에 대 한 포인터 `_AtlCreateWndData` 입니다.

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="see-also"></a>참고 항목

[클래스 및 구조체](../../atl/reference/atl-classes.md)
