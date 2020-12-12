---
description: '다음에 대 한 자세한 정보: _ATL_BASE_MODULE70 구조체'
title: _ATL_BASE_MODULE70 구조체
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
ms.openlocfilehash: 5bcf2083f9c8991871c05535fd3e20a39bfeb822
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165513"
---
# <a name="_atl_base_module70-structure"></a>_ATL_BASE_MODULE70 구조체

ATL을 사용 하는 모든 프로젝트에서 사용 됩니다.

## <a name="syntax"></a>구문

```cpp
struct _ATL_BASE_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInst;
    HINSTANCE m_hInstResource;
    bool m_bNT5orWin98;
    DWORD dwAtlBuildVer;
    GUID* pguidVer;
    CRITICAL_SECTION m_csResource;
    CSimpleArray<HINSTANCE> m_rgResourceInstance;
};
```

## <a name="members"></a>멤버

`cbSize`<br/>
버전 관리에 사용 되는 구조의 크기입니다.

`m_hInst`<br/>
`hInstance`이 모듈에 대 한입니다 (exe 또는 dll).

`m_hInstResource`<br/>
기본 인스턴스 리소스 핸들입니다.

`m_bNT5orWin98`<br/>
운영 체제 버전 정보입니다. ATL에서 내부적으로 사용 됩니다.

`dwAtlBuildVer`<br/>
ATL의 버전을 저장 합니다. 현재 0x0700입니다.

`pguidVer`<br/>
ATL의 내부 GUID입니다.

`m_csResource`<br/>
배열에 대 한 액세스를 동기화 하는 데 사용 `m_rgResourceInstance` 됩니다. ATL에서 내부적으로 사용 됩니다.

`m_rgResourceInstance`<br/>
ATL에서 인식 하는 모든 리소스 인스턴스에서 리소스를 검색 하는 데 사용 되는 배열입니다. ATL에서 내부적으로 사용 됩니다.

## <a name="remarks"></a>설명

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module) 은 _ATL_BASE_MODULE70의 typedef로 정의 됩니다.

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="see-also"></a>참고 항목

[클래스 및 구조체](../../atl/reference/atl-classes.md)
