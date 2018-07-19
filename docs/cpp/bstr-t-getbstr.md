---
title: _bstr_t::GetBSTR | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetBSTR
dev_langs:
- C++
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3041e8a4ece0ddff813b7ef9cd2ccb258e520a82
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940484"
---
# <a name="bstrtgetbstr"></a>_bstr_t::GetBSTR
**Microsoft 전용**  
  
 `BSTR`에 의해 래핑되는 `_bstr_t`의 시작 부분을 가리킵니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
BSTR& GetBSTR( );  
  
```  
  
## <a name="return-value"></a>반환 값  
 `BSTR`에 의해 래핑되는 `_bstr_t`의 시작 부분입니다.  
  
## <a name="remarks"></a>설명  
 `GetBSTR`는 `_bstr_t`을 공유하는 모든 `BSTR` 개체에 영향을 줍니다. 둘 이상의 `_bstr_t` 공유할 수는 `BSTR` 복사 생성자를 사용 하 여 및 및 **연산자 =** 합니다.  
  
## <a name="example"></a>예  
 참조 [_bstr_t:: assign](../cpp/bstr-t-assign.md) 사용 하는 예제 `GetBSTR`합니다.  
  
 **Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [_bstr_t 클래스](../cpp/bstr-t-class.md)