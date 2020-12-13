---
description: '자세한 정보: 컴파일러 오류 C2891'
title: 컴파일러 오류 C2891
ms.date: 11/04/2016
f1_keywords:
- C2891
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
ms.openlocfilehash: e546340d0ba035da50dd36b18b870b565b6e1bc9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337436"
---
# <a name="compiler-error-c2891"></a>컴파일러 오류 C2891

' parameter ': 템플릿 매개 변수의 주소를 가져올 수 없습니다.

Lvalue가 아닌 경우 템플릿 매개 변수의 주소를 가져올 수 없습니다. 형식 매개 변수는 주소가 없으므로 lvalue가 아닙니다. Lvalue가 아닌 템플릿 매개 변수 목록에서 형식이 아닌 값에도 주소가 없습니다. 이는 템플릿 매개 변수로 전달 된 값이 템플릿 인수의 컴파일러 생성 복사본 이기 때문에 컴파일러 오류 C2891를 발생 시킨 코드의 예입니다.

```
template <int i> int* f() { return &i; }
```

참조 형식과 같은 lvalues에 해당 하는 템플릿 매개 변수는 해당 주소를 가져올 수 있습니다.

```
template <int& r> int* f() { return &r; }
```

이 오류를 해결 하려면 lvalue가 아닌 경우 템플릿 매개 변수의 주소를 사용 하지 마십시오.
