---
title: _ATL_BASE_MODULE70 구조 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 484fc4a68d0421cb12e901b2d56f30e95f6cb79b
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34256420"
---
# <a name="atlbasemodule70-structure"></a>_ATL_BASE_MODULE70 구조
ATL.를 사용 하는 모든 프로젝트에서 사용  
  
## <a name="syntax"></a>구문  
  
```
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
 `cbSize`  
 버전 관리에 사용 되는 구조체의 크기입니다.  
  
 `m_hInst`  
 **hInstance** (exe 또는 dll)이이 모듈에 대 한 합니다.  
  
 `m_hInstResource`  
 기본 인스턴스 리소스 핸들입니다.  
  
 **m_bNT5orWin98**  
 운영 체제 버전 정보입니다. ATL.에서 내부적으로 사용  
  
 **dwAtlBuildVer**  
 ATL.의 버전을 저장 현재 0x0700 합니다.  
  
 **pguidVer**  
 ATL의 내부 GUID입니다.  
  
 **m_csResource**  
 에 대 한 액세스를 동기화 하는 데는 **m_rgResourceInstance** 배열입니다. ATL.에서 내부적으로 사용  
  
 **m_rgResourceInstance**  
 ATL를 인식 하는 모든 리소스 인스턴스에서 리소스를 검색 하는 데 사용 하는 배열입니다. ATL.에서 내부적으로 사용  
  
## <a name="remarks"></a>설명  
 [_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module) 의 typedef로 정의 된 `_ATL_BASE_MODULE70`합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atlcore.h  
  
## <a name="see-also"></a>참고 항목  
 [클래스 및 구조체](../../atl/reference/atl-classes.md)





