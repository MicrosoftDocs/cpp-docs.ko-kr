---
title: 'Comptr:: Asweak 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::AsWeak
dev_langs:
- C++
helpviewer_keywords:
- AsWeak method
ms.assetid: 23e29dcd-39cb-423f-abe6-6df4428213bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 78f6eb9f3d0acf6a28479593d64616fa6881be76
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648092"
---
# <a name="comptrasweak-method"></a>ComPtr::AsWeak 메서드
현재 개체에 대한 약한 참조를 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT AsWeak(  
   _Out_ WeakRef* pWeakRef  
);  
```  
  
### <a name="parameters"></a>매개 변수  
 *pWeakRef*  
 이 작업이 완료 될 때 약한 참조 개체에 대 한 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
 성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** client.h  
  
 **네임스페이스:** Microsoft::WRL  
  
## <a name="see-also"></a>참고 항목  
 [ComPtr 클래스](../windows/comptr-class.md)