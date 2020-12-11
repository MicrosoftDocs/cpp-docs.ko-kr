---
description: '다음에 대 한 자세한 정보: _ATL_FUNC_INFO 구조체'
title: _ATL_FUNC_INFO 구조체
ms.date: 11/04/2016
f1_keywords:
- _ATL_FUNC_INFO
- ATL::_ATL_FUNC_INFO
- ATL._ATL_FUNC_INFO
helpviewer_keywords:
- _ATL_FUNC_INFO structure
- ATL_FUNC_INFO structure
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
ms.openlocfilehash: 6368440347672524bb7d1e3aa3068ef91a2c6f09
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158857"
---
# <a name="_atl_func_info-structure"></a>_ATL_FUNC_INFO 구조체

의 메서드 또는 속성을 설명 하는 데 사용 되는 형식 정보를 포함 합니다.

## <a name="syntax"></a>구문

```cpp
struct _ATL_FUNC_INFO {
    CALLCONV cc;
    VARTYPE vtReturn;
    SHORT nParams;
    VARTYPE pVarTypes[_ATL_MAX_VARTYPES];
};
```

## <a name="members"></a>멤버

`cc`<br/>
호출 규칙. [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) 클래스와 함께이 구조체를 사용 하는 경우이 멤버를 CC_STDCALL 해야 합니다. `CC_CDECL` 는 구조체의 필드에 대해 Windows CE에서 유일 하 게 지원 되는 옵션입니다 `CALLCONV` `_ATL_FUNC_INFO` . 다른 모든 값은 지원 되지 않으므로 동작이 정의 되지 않습니다.

`vtReturn`<br/>
함수 반환 값의 변형 유형입니다.

`nParams`<br/>
함수 매개 변수 수입니다.

`pVarTypes`<br/>
함수 매개 변수의 variant 형식 배열입니다.

## <a name="remarks"></a>설명

내부적으로 ATL은이 구조체를 사용 하 여 형식 라이브러리에서 가져온 정보를 저장 합니다. [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) class 및 [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) 매크로와 함께 사용 되는 이벤트 처리기에 대 한 형식 정보를 제공 하는 경우이 구조체를 직접 조작 해야 할 수 있습니다.

## <a name="example"></a>예제

IDL에 정의 된에는 다음과 같이 정의 됩니다.

[!code-cpp[NVC_ATL_Windowing#139](../../atl/codesnippet/cpp/atl-func-info-structure_1.idl)]

구조를 정의 합니다 `_ATL_FUNC_INFO` .

[!code-cpp[NVC_ATL_Windowing#140](../../atl/codesnippet/cpp/atl-func-info-structure_2.h)]

## <a name="requirements"></a>요구 사항

헤더: atlcom.h

## <a name="see-also"></a>참고 항목

[클래스 및 구조체](../../atl/reference/atl-classes.md)<br/>
[IDispEventSimpleImpl 클래스](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)
