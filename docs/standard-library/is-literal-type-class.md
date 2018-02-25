---
title: "is_literal_type 클래스 | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_literal_type
dev_langs:
- C++
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 09a1531458df692be2b78a97a1723366f912d087
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="isliteraltype-class"></a>is_literal_type 클래스
형식을 `constexpr` 변수로 사용하거나, `constexpr` 함수에서 생성, 사용 또는 반환할 수 있는지를 테스트합니다.  
  
## <a name="syntax"></a>구문  
  
```
template <class T>  
struct is_literal_type;
```  
  
#### <a name="parameters"></a>매개 변수  
 `T`  
 형식이 쿼리입니다.  
  
## <a name="remarks"></a>설명  
 형식 조건자의 인스턴스는 `T` 형식이 *리터럴 형식*인 경우 true이고, 그렇지 않으면 false입니다. 리터럴 형식은 `void`, 스칼라 형식, 참조 형식, 리터럴 형식의 배열 또는 리터럴 클래스 형식입니다. 리터럴 클래스 형식은 trivial 소멸자가 있거나, 집계 형식이거나, 이동하거나 복사할 수 없는 하나 이상의 `constexpr` 생성자가 있는 클래스 형식이며 모든 기본 클래스 및 비정적 데이터 멤버는 비휘발성 리터럴 형식입니다. literal의 형식은 항상 리터럴 형식이지만 리터럴 형식의 개념에는 컴파일러가 컴파일 시간에 `constexpr`로 평가할 수 있는 모든 항목이 포함됩니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<type_traits>  
  
 **네임스페이스:** std  
  
## <a name="see-also"></a>참고 항목  
 [<type_traits>](../standard-library/type-traits.md)



