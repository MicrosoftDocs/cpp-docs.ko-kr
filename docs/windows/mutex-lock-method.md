---
title: 'Mutex:: lock 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 61d95072-b690-441e-a080-0bf94a733141
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 37044dbd884c4e38c70677bf9a8fa0a51fda0a88
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880874"
---
# <a name="mutexlock-method"></a>Mutex::Lock 메서드
현재 개체 또는 지정 된 핸들과 연결 된 뮤텍스 개체 될 때까지 대기는 뮤텍스를 해제 하거나 지정한 시간 제한 간격이 경과 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
SyncLock Lock(  
   DWORD milliseconds = INFINITE  
);  
  
static SyncLock Lock(  
   HANDLE h,  
   DWORD milliseconds = INFINITE  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `milliseconds`  
 제한 시간 간격(밀리초)입니다. 기본값은 INFINITE으로, 무제한 대기합니다.  
  
 `h`  
 뮤텍스 개체의 핸들입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>참고 항목
 [Mutex 클래스](../windows/mutex-class1.md)