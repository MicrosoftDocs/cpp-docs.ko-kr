---
title: "Asyncbase:: Close 메서드 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: a52b1124-754b-4393-b491-64aae0c22f1c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 35b7fda0ab10ff80df0f4a27f6e79028e73574fa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbaseclose-method"></a>AsyncBase::Close 메서드
비동기 작업을 닫습니다.  
  
## <a name="syntax"></a>구문  
  
```  
STDMETHOD(  
   Close  
)(void) override;  
```  
  
## <a name="return-value"></a>반환 값  
 작업을 닫거나 이미 하면 s_ok이 고; 닫힙니다. 그렇지 않으면 E_ILLEGAL_STATE_CHANGE 합니다.  
  
## <a name="remarks"></a>설명  
 Close (), IAsyncInfo::Close의 기본 구현을 이며 실제로 진행 되지 않습니다. 비동기 작업을 실제로 닫으려면 OnClose() 순수 가상 메서드를 재정의 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** async.h  
  
 **네임스페이스:** Microsoft::WRL  
  
## <a name="see-also"></a>참고 항목  
 [AsyncBase 클래스](../windows/asyncbase-class.md)