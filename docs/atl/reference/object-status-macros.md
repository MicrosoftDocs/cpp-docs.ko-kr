---
title: 개체 상태 매크로
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: 9c4df80b2b9828077ec3738bc296f19aadf2df68
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658954"
---
# <a name="object-status-macros"></a>개체 상태 매크로

이 매크로 ActiveX 컨트롤에 속하는 플래그를 설정 합니다.

|||
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|ATL ActiveX 컨트롤의 OLEMISC 플래그를 설정 하는 데 사용 합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** atlcom.h

##  <a name="declare_olemisc_status"></a>  DECLARE_OLEMISC_STATUS

ATL ActiveX 컨트롤의 OLEMISC 플래그를 설정 하는 데 사용 합니다.

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>매개 변수

*miscstatus*<br/>
해당 되는 모든 OLEMISC 플래그입니다.

### <a name="remarks"></a>설명

이 매크로 ActiveX 컨트롤에 대 한 OLEMISC 플래그를 설정 하는 데 사용 됩니다. 가리킵니다 [IOleObject::GetMiscStatus](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) 대 한 자세한 내용은 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>참고 항목

[매크로](../../atl/reference/atl-macros.md)
