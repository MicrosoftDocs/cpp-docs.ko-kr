---
description: '자세히 알아보기: 속성 맵 매크로'
title: 속성 맵 매크로
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_PROP_MAP
- atlcom/ATL::PROP_DATA_ENTRY
- atlcom/ATL::PROP_ENTRY_TYPE
- atlcom/ATL::PROP_ENTRY_TYPE_EX
- atlcom/ATL::PROP_PAGE
- atlcom/ATL::END_PROP_MAP
helpviewer_keywords:
- property maps
ms.assetid: 128bc742-2b98-4b97-a243-684dbb83db77
ms.openlocfilehash: b2fc7f96c42d7f9d3f116f13c9864ce857e32743
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157804"
---
# <a name="property-map-macros"></a>속성 맵 매크로

이러한 매크로는 속성 맵과 항목을 정의 합니다.

|Name|설명|
|-|-|
|[BEGIN_PROP_MAP](#begin_prop_map)|ATL 속성 맵의 시작을 표시 합니다.|
|[PROP_DATA_ENTRY](#prop_data_entry)|ActiveX 컨트롤의 범위 또는 크기를 나타냅니다.|
|[PROP_ENTRY_TYPE](#prop_entry_type)|속성 설명, 속성 DISPID 및 속성 페이지 CLSID를 속성 맵에 입력 합니다.|
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|속성 설명, 속성 DISPID, 속성 페이지 CLSID 및 `IDispatch` IID를 속성 맵에 입력 합니다.|
|[PROP_PAGE](#prop_page)|속성 맵에 속성 페이지 CLSID를 입력 합니다.|
|[END_PROP_MAP](#end_prop_map)|ATL 속성 맵의 끝을 표시 합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="begin_prop_map"></a><a name="begin_prop_map"></a> BEGIN_PROP_MAP

개체의 속성 맵의 시작을 표시 합니다.

```
BEGIN_PROP_MAP(theClass)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
진행 속성 맵을 포함 하는 클래스를 지정 합니다.

### <a name="remarks"></a>설명

속성 맵은 속성 설명, 속성 Dispid, 속성 페이지 Clsid 및 iid를 저장 합니다 `IDispatch` . [IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md), [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md), [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)및 [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) 클래스는 속성 맵을 사용 하 여이 정보를 검색 하 고 설정 합니다.

ATL 프로젝트 마법사를 사용 하 여 개체를 만드는 경우 마법사는 BEGIN_PROP_MAP를 지정 하 고 [END_PROP_MAP](#end_prop_map)를 지정 하 여 빈 속성 맵을 만듭니다.

속성 맵을 사용 하는 개체에 사용자 인터페이스가 없을 수 있으므로 속성 맵의 범위 (즉, 차원)를 저장 하지 않으므로, 범위를 갖지 않습니다. BEGIN_PROP_MAP 개체가 사용자 인터페이스를 사용 하는 ActiveX 컨트롤이 면 범위를 가집니다. 이 경우에는 속성 맵에 [PROP_DATA_ENTRY](#prop_data_entry) 지정 하 여 범위를 제공 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]

## <a name="prop_data_entry"></a><a name="prop_data_entry"></a> PROP_DATA_ENTRY

ActiveX 컨트롤의 범위 또는 크기를 나타냅니다.

```
PROP_DATA_ENTRY( szDesc, member, vt)
```

### <a name="parameters"></a>매개 변수

*szDesc*<br/>
진행 속성 설명입니다.

*구성원과*<br/>
진행 익스텐트를 포함 하는 데이터 멤버입니다. 예를 들면 `m_sizeExtent` 입니다.

*vt*<br/>
진행 속성의 변형 유형을 지정 합니다.

### <a name="remarks"></a>설명

이 매크로는 지정 된 데이터 멤버가 유지 되도록 합니다.

ActiveX 컨트롤을 만들면 마법사는 속성 맵 매크로 [BEGIN_PROP_MAP](#begin_prop_map) 다음에이 매크로를 삽입 하 고 속성 맵 매크로 [END_PROP_MAP](#end_prop_map)앞에 삽입 합니다.

### <a name="example"></a>예제

다음 예제에서는 개체 ()의 범위가 `m_sizeExtent` 유지 되 고 있습니다.

[!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]

[!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]

## <a name="prop_entry_type"></a><a name="prop_entry_type"></a> PROP_ENTRY_TYPE

이 매크로를 사용 하 여 속성 설명, 속성 DISPID 및 속성 페이지 CLSID를 개체의 속성 맵에 입력할 수 있습니다.

```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```

### <a name="parameters"></a>매개 변수

*szDesc*<br/>
진행 속성 설명입니다.

*dispid*<br/>
진행 속성의 DISPID입니다.

*가*<br/>
진행 연결 된 속성 페이지의 CLSID입니다. 연결 된 속성 페이지가 없는 속성에 CLSID_NULL 특수 값을 사용 합니다.

*vt*<br/>
진행 속성의 형식입니다.

### <a name="remarks"></a>설명

PROP_ENTRY 매크로는 안전 하지 않으며 사용 되지 않습니다. PROP_ENTRY_TYPE로 대체 되었습니다.

[BEGIN_PROP_MAP](#begin_prop_map) 매크로는 속성 맵의 시작을 표시 합니다. [END_PROP_MAP](#end_prop_map) 매크로는 끝을 표시 합니다.

### <a name="example"></a>예제

[BEGIN_PROP_MAP](#begin_prop_map)의 예제를 참조 하세요.

## <a name="prop_entry_type_ex"></a><a name="prop_entry_type_ex"></a> PROP_ENTRY_TYPE_EX

[PROP_ENTRY_TYPE](#prop_entry_type)와 유사 하지만 개체가 여러 이중 인터페이스를 지 원하는 경우에는 특정 IID를 지정할 수 있습니다.

```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```

### <a name="parameters"></a>매개 변수

*szDesc*<br/>
진행 속성 설명입니다.

*dispid*<br/>
진행 속성의 DISPID입니다.

*가*<br/>
진행 연결 된 속성 페이지의 CLSID입니다. 연결 된 속성 페이지가 없는 속성에 CLSID_NULL 특수 값을 사용 합니다.

*iidDispatch*<br/>
진행 속성을 정의 하는 이중 인터페이스의 IID입니다.

*vt*<br/>
진행 속성의 형식입니다.

### <a name="remarks"></a>설명

PROP_ENTRY_EX 매크로는 안전 하지 않으며 사용 되지 않습니다. PROP_ENTRY_TYPE_EX로 대체 되었습니다.

[BEGIN_PROP_MAP](#begin_prop_map) 매크로는 속성 맵의 시작을 표시 합니다. [END_PROP_MAP](#end_prop_map) 매크로는 끝을 표시 합니다.

### <a name="example"></a>예제

다음 예에서는에 대 한 항목 뒤에 항목을 그룹화 `IMyDual1` `IMyDual2` 합니다. 이중 인터페이스를 기준으로 그룹화 하면 성능이 향상 됩니다.

[!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]

## <a name="prop_page"></a><a name="prop_page"></a> PROP_PAGE

이 매크로를 사용 하 여 개체의 속성 맵에 속성 페이지 CLSID를 입력할 수 있습니다.

```
PROP_PAGE(clsid)
```

### <a name="parameters"></a>매개 변수

*가*<br/>
진행 속성 페이지의 CLSID입니다.

### <a name="remarks"></a>설명

PROP_PAGE은 [PROP_ENTRY_TYPE](#prop_entry_type)와 비슷하지만 속성 설명 또는 DISPID는 필요 하지 않습니다.

> [!NOTE]
> PROP_ENTRY_TYPE 또는 [PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)를 사용 하 여 CLSID를 이미 입력 한 경우에는 PROP_PAGE를 사용 하 여 추가 항목을 만들 필요가 없습니다.

[BEGIN_PROP_MAP](#begin_prop_map) 매크로는 속성 맵의 시작을 표시 합니다. [END_PROP_MAP](#end_prop_map) 매크로는 끝을 표시 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]

## <a name="end_prop_map"></a><a name="end_prop_map"></a> END_PROP_MAP

개체의 속성 맵의 끝을 표시 합니다.

```
END_PROP_MAP()
```

### <a name="remarks"></a>설명

ATL 프로젝트 마법사를 사용 하 여 개체를 만드는 경우 마법사는 [BEGIN_PROP_MAP](#begin_prop_map) 를 지정 하 고 END_PROP_MAP를 지정 하 여 빈 속성 맵을 만듭니다.

### <a name="example"></a>예제

[BEGIN_PROP_MAP](#begin_prop_map)의 예제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[매크로](../../atl/reference/atl-macros.md)
