---
title: _bstr_t::GetAddress | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetAddress
dev_langs:
- C++
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 680588a4c045c20001b46b35c67d28e366afc52d
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/13/2018
ms.locfileid: "42571603"
---
# <a name="bstrtgetaddress"></a>_bstr_t::GetAddress
**Microsoft 전용**  
  
 기존 문자열을 해제하고 새로 할당된 문자열의 주소를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
BSTR* GetAddress( );  
```  
  
## <a name="return-value"></a>반환 값  
 `BSTR`로 래핑되는 `_bstr_t`에 대한 포인터입니다.  
  
## <a name="remarks"></a>설명  
 **GetAddress** 모두에 영향을 줍니다 `_bstr_t` 공유 하는 개체는 `BSTR`합니다. 둘 이상의 `_bstr_t` 공유할 수는 `BSTR` 복사 생성자를 사용 하 여 및 **연산자 =** 합니다.  
  
## <a name="example"></a>예  
 참조 [_bstr_t:: assign](../cpp/bstr-t-assign.md) 사용 하는 예제 **GetAddress**합니다.  
  
 **Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고자료  
 [_bstr_t 클래스](../cpp/bstr-t-class.md)