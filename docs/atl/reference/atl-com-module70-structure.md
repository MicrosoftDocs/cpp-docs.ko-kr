---
description: '다음에 대 한 자세한 정보: _ATL_COM_MODULE70 구조체'
title: _ATL_COM_MODULE70 구조체
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
ms.openlocfilehash: db2139d1c816c13e6da104f6a6d785ef35a07721
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165410"
---
# <a name="_atl_com_module70-structure"></a>_ATL_COM_MODULE70 구조체

ATL의 COM 관련 코드에서 사용 됩니다.

## <a name="syntax"></a>구문

```cpp
struct _ATL_COM_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInstTypeLib;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapFirst;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapLast;
    CRITICAL_SECTION m_csObjMap;
};
```

## <a name="members"></a>멤버

`cbSize`<br/>
버전 관리에 사용 되는 구조의 크기입니다.

`m_hInstTypeLib`<br/>
이 모듈의 형식 라이브러리에 대 한 핸들 인스턴스입니다.

`m_ppAutoObjMapFirst`<br/>
이 모듈에 대 한 개체 맵 항목의 시작을 나타내는 배열 요소의 주소입니다.

`m_ppAutoObjMapLast`<br/>
이 모듈에 대 한 개체 맵 항목의 끝을 나타내는 배열 요소의 주소입니다.

`m_csObjMap`<br/>
개체 맵 항목에 대 한 액세스를 serialize 하는 임계 영역입니다. ATL에서 내부적으로 사용 됩니다.

## <a name="remarks"></a>설명

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module) 은 _ATL_COM_MODULE70의 typedef로 정의 됩니다.

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="see-also"></a>참고 항목

[클래스 및 구조체](../../atl/reference/atl-classes.md)
