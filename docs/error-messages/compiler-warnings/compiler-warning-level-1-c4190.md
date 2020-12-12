---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4190'
title: 컴파일러 경고 (수준 1) C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: ff27d5913e23fa1488816b3e2bb7284440c7577b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266587"
---
# <a name="compiler-warning-level-1-c4190"></a>컴파일러 경고 (수준 1) C4190

' identifier1 '에 C 링크를 지정 했으나 C와 호환 되지 않는 UDT ' identifier2 '를 반환 합니다.

함수 또는 함수 포인터에 UDT (클래스, 구조체, 열거형 또는 공용 구조체 인 사용자 정의 형식)가 반환 형식 및 링크로 포함 되어 `extern "C"` 있습니다. 이는 다음과 같은 경우에 유효 합니다.

- 이 함수에 대 한 모든 호출은 c + +에서 발생 합니다.

- 함수 정의는 c + +입니다.

## <a name="example"></a>예제

```cpp
// C4190.cpp
// compile with: /W1 /LD
struct X
{
   int i;
   X ();
   virtual ~X ();
};

extern "C" X func ();   // C4190
```
