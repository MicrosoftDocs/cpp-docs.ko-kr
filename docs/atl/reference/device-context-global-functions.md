---
title: 장치 컨텍스트 전역 함수 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
dev_langs:
- C++
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37d54fbe9391cb53cca1d84401e90bb6fd47a479
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358591"
---
# <a name="device-context-global-functions"></a>장치 컨텍스트 전역 함수
이 함수는 지정된 된 장치에 대 한 장치 컨텍스트를 만듭니다.  
  
|||  
|-|-|  
|[AtlCreateTargetDC](#atlcreatetargetdc)|장치 컨텍스트를 만듭니다.|  
  
##  <a name="atlcreatetargetdc"></a>  AtlCreateTargetDC  
 에 지정 된 장치에 대 한 장치 컨텍스트를 만듭니다.는 [DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) 구조입니다.  
  
```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```  
  
### <a name="parameters"></a>매개 변수  
 *hdc*  
 [in] 장치 컨텍스트에의 기존 핸들 또는 **NULL**합니다.  
  
 `ptd`  
 [in] 에 대 한 포인터는 **DVTARGETDEVICE** 대상 장치에 대 한 정보가 포함 된 구조체입니다.  
  
### <a name="return-value"></a>반환 값  
 에 지정 된 장치에 대 한 장치 컨텍스트를 핸들을 반환 합니다.는 **DVTARGETDEVICE**합니다. 장치는 지정 하는 경우 기본 디스플레이 장치에 핸들을 반환 합니다.  
  
### <a name="remarks"></a>설명  
 구조가 **NULL** 및 *hdc* 은 **NULL**, 기본 디스플레이 장치에 대 한 장치 컨텍스트를 만듭니다.  
  
 경우 *hdc* 않습니다 **NULL** 및 `ptd` 은 **NULL**, 함수 반환 기존 *hdc*합니다.  

## <a name="requirements"></a>요구 사항  
 **헤더:** atlwin.h  
   
## <a name="see-also"></a>참고 항목  
 [함수](../../atl/reference/atl-functions.md)
