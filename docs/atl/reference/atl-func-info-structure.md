---
title: _ATL_FUNC_INFO 구조 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- _ATL_FUNC_INFO
- ATL::_ATL_FUNC_INFO
- ATL._ATL_FUNC_INFO
dev_langs:
- C++
helpviewer_keywords:
- _ATL_FUNC_INFO structure
- ATL_FUNC_INFO structure
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa81e83d353c542ea5b2b6e8e5e8fe32f7c57606
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
---
# <a name="atlfuncinfo-structure"></a>_ATL_FUNC_INFO 구조
dispinterface에 메서드 또는 속성을 설명 하는 데 사용 되는 형식 정보를 포함 합니다.  
  
## <a name="syntax"></a>구문  
  
```
struct _ATL_FUNC_INFO {
    CALLCONV cc;
    VARTYPE vtReturn;
    SHORT nParams;
    VARTYPE pVarTypes[_ATL_MAX_VARTYPES];
};
```  
  
## <a name="members"></a>멤버  
 **cc**  
 호출 규칙. 와이 구조를 사용 하는 경우는 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) 클래스를이 멤버 있어야 **CC_STDCALL**합니다. `CC_CDECL` 에 대 한 Windows CE에서는 지원 되는 옵션만 `CALLCONV` 필드는 `_ATL_FUNC_INFO` 구조입니다. 다른 모든 값 지원 되지 않습니다. 따라서 해당 동작은 정의 되지 않았습니다.  
  
 **vtReturn**  
 값을 반환 하는 함수의 variant 유형입니다.  
  
 **nParams**  
 함수 매개 변수의 수입니다.  
  
 **pVarTypes**  
 함수 매개 변수의 variant 형식의 배열입니다.  
  
## <a name="remarks"></a>설명  
 내부적으로 ATL이이 구조를 사용 하 여 형식 라이브러리에서 얻은 정보를 저장 합니다. 함께 사용 하는 이벤트 처리기에 대 한 형식 정보를 제공 하는 경우이 구조를 직접 조작 해야 할 수 있습니다는 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) 클래스 및 [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) 매크로입니다.  
  
## <a name="example"></a>예제  
 IDL에 정의 하는 dispinterface 메서드를 제공 합니다.  
  
 [!code-cpp[NVC_ATL_Windowing#139](../../atl/codesnippet/cpp/atl-func-info-structure_1.idl)]  
  
 정의 하는 `_ATL_FUNC_INFO` 구조:  
  
 [!code-cpp[NVC_ATL_Windowing#140](../../atl/codesnippet/cpp/atl-func-info-structure_2.h)]  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atlcom.h  
  
## <a name="see-also"></a>참고 항목  
  [클래스 및 구조체](../../atl/reference/atl-classes.md)  
 [IDispEventSimpleImpl 클래스](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)





