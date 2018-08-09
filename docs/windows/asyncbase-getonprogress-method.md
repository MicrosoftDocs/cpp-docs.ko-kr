---
title: 'Asyncbase:: Getonprogress 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::GetOnProgress
dev_langs:
- C++
helpviewer_keywords:
- GetOnProgress method
ms.assetid: 286ddc9c-3e30-41a2-8e8b-e53d3fb0649d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9446c94039db0ff81826e77d71a2a9539be4b276
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643149"
---
# <a name="asyncbasegetonprogress-method"></a>AsyncBase::GetOnProgress 메서드
지정된 된 변수를 현재 진행률 이벤트 처리기의 주소를 복사합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
STDMETHOD(  
   GetOnProgress  
)(TProgress** progressHandler);  
```  
  
### <a name="parameters"></a>매개 변수  
 *progressHandler*  
 현재 진행률 이벤트 처리기의 주소를 저장 된 위치입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 s_ok이 고 그렇지 않으면 E_ILLEGAL_METHOD_CALL 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** async.h  
  
 **네임스페이스:** Microsoft::WRL  
  
## <a name="see-also"></a>참고 항목  
 [AsyncBase 클래스](../windows/asyncbase-class.md)