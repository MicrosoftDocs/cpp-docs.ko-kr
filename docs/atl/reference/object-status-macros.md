---
description: '자세한 정보: 개체 상태 매크로'
title: 개체 상태 매크로
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: 7aac547ac0b63a7db9ceea3b58befdea3e076f3f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157908"
---
# <a name="object-status-macros"></a>개체 상태 매크로

이 매크로는 ActiveX 컨트롤에 속하는 플래그를 설정 합니다.

|Name|설명|
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|ATL ActiveX 컨트롤에서 OLEMISC 플래그를 설정 하는 데 사용 됩니다.|

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="declare_olemisc_status"></a><a name="declare_olemisc_status"></a> DECLARE_OLEMISC_STATUS

ATL ActiveX 컨트롤에서 OLEMISC 플래그를 설정 하는 데 사용 됩니다.

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>매개 변수

*miscstatus*<br/>
모든 적용 가능한 OLEMISC 플래그입니다.

### <a name="remarks"></a>설명

이 매크로는 ActiveX 컨트롤에 대 한 OLEMISC 플래그를 설정 하는 데 사용 됩니다. 자세한 내용은 [IOleObject:: GetMiscStatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) 를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>참고 항목

[매크로](../../atl/reference/atl-macros.md)
