---
description: '자세한 정보: COM 맵 매크로'
title: COM 맵 매크로
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: 076a13418a48147654862c2b5a26688b195d5252
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141325"
---
# <a name="com-map-macros"></a>COM 맵 매크로

이러한 매크로는 COM 인터페이스 맵을 정의 합니다.

|매크로|설명|
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|COM 인터페이스 맵 항목의 시작을 표시 합니다.|
|[END_COM_MAP](#end_com_map)|COM 인터페이스 맵 항목의 끝을 표시 합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="begin_com_map"></a><a name="begin_com_map"></a> BEGIN_COM_MAP

COM 맵은 개체의 인터페이스를를 통해 클라이언트에 노출 하는 메커니즘입니다 `QueryInterface` .

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>매개 변수

*x*<br/>
진행 인터페이스를 노출 하는 클래스 개체의 이름입니다.

### <a name="remarks"></a>설명

[CComObjectRootEx:: InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) 는 COM 맵의 인터페이스에 대 한 포인터만 반환 합니다. BEGIN_COM_MAP 매크로를 사용 하 여 인터페이스 맵을 시작 하 고, [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) 매크로 또는 해당 변형 중 하나를 사용 하 여 각 인터페이스에 대 한 항목을 추가 하 고, [END_COM_MAP](#end_com_map) 매크로를 사용 하 여 맵을 완료 합니다.

### <a name="example"></a>예제

ATL [BEEPER](../../overview/visual-cpp-samples.md) 샘플:

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

## <a name="end_com_map"></a><a name="end_com_map"></a> END_COM_MAP

COM 인터페이스 맵의 정의를 종료 합니다.

```
END_COM_MAP()
```

## <a name="see-also"></a>참고 항목

[매크로](../../atl/reference/atl-macros.md)<br/>
[COM 맵 전역 함수](../../atl/reference/com-map-global-functions.md)
