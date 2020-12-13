---
description: '자세히 알아보기: 합성 컨트롤 매크로'
title: 복합 컨트롤 매크로
ms.date: 05/06/2019
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
ms.openlocfilehash: 0107f91350516bd0f7e35cf82a49f79ff3c5797e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141195"
---
# <a name="composite-control-macros"></a>복합 컨트롤 매크로

이러한 매크로는 이벤트 싱크 맵과 항목을 정의 합니다.

|매크로|설명|
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|복합 컨트롤에 대 한 이벤트 싱크 맵의 시작을 표시 합니다.|
|[END_SINK_MAP](#end_sink_map)|복합 컨트롤에 대 한 이벤트 싱크 맵의 끝을 표시 합니다.|
|[SINK_ENTRY](#sink_entry)|이벤트 싱크 맵에 대 한 항목입니다.|
|[SINK_ENTRY_EX](#sink_entry_ex)|추가 매개 변수를 사용 하 여 이벤트 싱크 맵에 대 한 항목입니다.|
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (Visual Studio 2017) Iid에 대 한 포인터를 사용 한다는 점을 제외 하 고 SINK_ENTRY_EX와 비슷합니다.|
|[SINK_ENTRY_INFO](#sink_entry_info)|[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)와 함께 사용 하기 위해 수동으로 제공한 유형 정보를 사용 하 여 이벤트 싱크 맵에 대 한 항목입니다.|
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (Visual Studio 2017) Iid에 대 한 포인터를 사용 한다는 점을 제외 하 고 SINK_ENTRY_INFO와 비슷합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="begin_sink_map"></a><a name="begin_sink_map"></a> BEGIN_SINK_MAP

복합 컨트롤에 대 한 이벤트 싱크 맵의 시작을 선언 합니다.

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>매개 변수

*_class*<br/>
진행 컨트롤을 지정 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>설명

ActiveX 이벤트 싱크에 대 한 CE ATL 구현은 이벤트 처리기 메서드에서 HRESULT 또는 void 형식의 반환 값만 지원 합니다. 다른 모든 반환 값은 지원 되지 않으며 해당 동작은 정의 되지 않습니다.

## <a name="end_sink_map"></a><a name="end_sink_map"></a> END_SINK_MAP

복합 컨트롤에 대 한 이벤트 싱크 맵의 끝을 선언 합니다.

```
END_SINK_MAP()
```

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>설명

ActiveX 이벤트 싱크에 대 한 CE ATL 구현은 이벤트 처리기 메서드에서 HRESULT 또는 void 형식의 반환 값만 지원 합니다. 다른 모든 반환 값은 지원 되지 않으며 해당 동작은 정의 되지 않습니다.

## <a name="sink_entry"></a><a name="sink_entry"></a> SINK_ENTRY

*Id* 로 식별 되는 컨트롤의 지정 된 이벤트 (*dispid*)에 대해 처리기 함수 (*fn*)를 선언 합니다.

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>매개 변수

*id*<br/>
진행 컨트롤을 식별 합니다.

*dispid*<br/>
진행 지정 된 이벤트를 식별 합니다.

*fn*<br/>
진행 이벤트 처리기 함수의 이름입니다. 이 함수는 `_stdcall` 호출 규칙을 사용 하 고 적절 한 대/소문자 스타일 서명을 사용 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>설명

ActiveX 이벤트 싱크에 대 한 CE ATL 구현은 이벤트 처리기 메서드에서 HRESULT 또는 void 형식의 반환 값만 지원 합니다. 다른 모든 반환 값은 지원 되지 않으며 해당 동작은 정의 되지 않습니다.

## <a name="sink_entry_ex-and-sink_entry_ex_p"></a><a name="sink_entry_ex"></a> SINK_ENTRY_EX 및 SINK_ENTRY_EX_P

*Id* 로 식별 되는 컨트롤에 대해 *iid*(디스패치 인터페이스)의 지정 된 이벤트 (*dispid*)에 대 한 처리기 함수 (*fn*)를 선언 합니다.

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>매개 변수

*id*<br/>
진행 컨트롤을 식별 합니다.

*iid*<br/>
진행 디스패치 인터페이스를 식별 합니다.

*piid*<br/>
진행 디스패치 인터페이스에 대 한 포인터입니다.

*dispid*<br/>
진행 지정 된 이벤트를 식별 합니다.

*fn*<br/>
진행 이벤트 처리기 함수의 이름입니다. 이 함수는 `_stdcall` 호출 규칙을 사용 하 고 적절 한 대/소문자 스타일 서명을 사용 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>설명

ActiveX 이벤트 싱크에 대 한 CE ATL 구현은 이벤트 처리기 메서드에서 HRESULT 또는 void 형식의 반환 값만 지원 합니다. 다른 모든 반환 값은 지원 되지 않으며 해당 동작은 정의 되지 않습니다.

## <a name="sink_entry_info-and-sink_entry_info_p"></a><a name="sink_entry_info"></a> SINK_ENTRY_INFO 및 SINK_ENTRY_INFO_P

이벤트 싱크 맵 내의 SINK_ENTRY_INFO 매크로를 사용 하 여 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) 에서 이벤트를 관련 처리기 함수로 라우팅하는 데 필요한 정보를 제공 합니다.

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>매개 변수

*id*<br/>
진행 이벤트 소스를 식별 하는 부호 없는 정수입니다. 이 값은 관련 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) 기본 클래스에서 사용 된 *nID* 템플릿 매개 변수와 일치 해야 합니다.

*iid*<br/>
진행 디스패치 인터페이스를 식별 하는 IID입니다.

*piid*<br/>
진행 디스패치 인터페이스를 식별 하는 IID에 대 한 포인터입니다.

*dispid*<br/>
진행 지정 된 이벤트를 식별 하는 DISPID입니다.

*fn*<br/>
진행 이벤트 처리기 함수의 이름입니다. 이 함수는 `_stdcall` 호출 규칙을 사용 하 고 적절 한 대/소문자 스타일 서명을 사용 해야 합니다.

*나타납니다*<br/>
진행 이벤트 처리기 함수에 대 한 정보를 입력 합니다. 이 형식 정보는 구조체에 대 한 포인터 형식으로 제공 됩니다 `_ATL_FUNC_INFO` . CC_CDECL는 구조체의 CALLCONV 필드에 대해 Windows CE에서 유일 하 게 지원 되는 옵션입니다 `_ATL_FUNC_INFO` . 다른 모든 값은 지원 되지 않으므로 동작이 정의 되지 않습니다.

### <a name="remarks"></a>설명

처음 네 개의 매크로 매개 변수는 [SINK_ENTRY_EX](#sink_entry_ex) 매크로와 동일 합니다. Final 매개 변수는 이벤트에 대 한 형식 정보를 제공 합니다. ActiveX 이벤트 싱크에 대 한 CE ATL 구현은 이벤트 처리기 메서드에서 HRESULT 또는 void 형식의 반환 값만 지원 합니다. 다른 모든 반환 값은 지원 되지 않으며 해당 동작은 정의 되지 않습니다.

## <a name="see-also"></a>참고 항목

[매크로](../../atl/reference/atl-macros.md)<br/>
[복합 컨트롤 전역 함수](../../atl/reference/composite-control-global-functions.md)
