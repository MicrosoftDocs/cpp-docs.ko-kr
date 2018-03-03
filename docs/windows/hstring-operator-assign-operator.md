---
title: "Hstring:: Operator = 연산자 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
dev_langs:
- C++
ms.assetid: 8e68c1ff-bc57-4526-810e-af3c284b4e30
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5abaa00030b301607c19def42920cb01eb72600a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="hstringoperator-operator"></a>HString::Operator= 연산자
현재 HString 개체가 다른 HString 개체의 값을 이동합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HString& operator=(HString&& other) throw()  
```  
  
#### <a name="parameters"></a>매개 변수  
 `other`  
 기존 HString 개체입니다.  
  
## <a name="remarks"></a>설명  
 기존 값 `other` 개체는 현재 HString 개체에 복사 차례로 `other` 개체를 제거 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>참고 항목  
 [HString 클래스](../windows/hstring-class.md)