---
title: _ATL_WIN_MODULE70 구조 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- _ATL_WIN_MODULE70
- ATL::_ATL_WIN_MODULE70
- ATL._ATL_WIN_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- _ATL_WIN_MODULE70 structure
- ATL_WIN_MODULE70 structure
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 587b115c428b0d82183abbec9f712ff06ea448f4
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="atlwinmodule70-structure"></a>_ATL_WIN_MODULE70 구조
Atl에서 창 작업 코드에서 사용 하는  
  
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
 `cbSize`  
 버전 관리에 사용 되는 구조체의 크기입니다.  
  
 `m_csWindowCreate`  
 창 등록 코드에 대 한 액세스를 serialize 하는 데 사용 합니다. ATL.에서 내부적으로 사용  
  
 **m_pCreateWndList**  
 해당 개체에 windows를 바인딩하는 데 사용 합니다. ATL.에서 내부적으로 사용  
  
 **m_rgWindowClassAtoms**  
 종료 시 제대로 등록 되지 될 수 있도록 창 클래스 등록을 추적 하는 데 사용 합니다. ATL.에서 내부적으로 사용  
  
## <a name="remarks"></a>설명  
 [_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module) 의 typedef로 정의 된 `_ATL_WIN_MODULE70`합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atlbase.h  
  
## <a name="see-also"></a>참고 항목  
 [클래스 및 구조체](../../atl/reference/atl-classes.md)





