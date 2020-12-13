---
description: '자세한 정보: 컴파일러 경고 C4430'
title: 컴파일러 경고 C4430
ms.date: 11/04/2016
f1_keywords:
- C4430
helpviewer_keywords:
- C4430
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
ms.openlocfilehash: af214bb0e9d373ee319008f509ba78f5d7ade38b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344304"
---
# <a name="compiler-warning-c4430"></a>컴파일러 경고 C4430

형식 지정자가 없습니다. int로 가정합니다. 참고: c + +는 기본-int를 지원 하지 않습니다.

이 오류는 Visual Studio 2005에 대해 수행한 컴파일러 규칙 작업의 결과로 생성 될 수 있습니다. 모든 선언에서 명시적으로 형식을 지정 해야 합니다. int는 더 이상 가정 되지 않습니다.

C4430는 항상 오류로 실행 됩니다.  또는/wd를 사용 하 여이 경고를 해제할 수 있습니다 `#pragma warning` . 자세한 내용은 [경고](../../preprocessor/warning.md) 또는 [/W,/W0,/W1,/W2,](../../build/reference/compiler-option-warning-level.md) /W3,/W4,/W1,/W2,/W3,/W4,/Wall,/wd,/we,/wo,/Wv,/wx (경고 수준)를 참조 하십시오. 

## <a name="example"></a>예제

다음 샘플에서는 C4430를 생성 합니다.

```cpp
// C4430.cpp
// compile with: /c
struct CMyClass {
   CUndeclared m_myClass;  // C4430
   int m_myClass;  // OK
};

typedef struct {
   POINT();   // C4430
   // try the following line instead
   // int POINT();
   unsigned x;
   unsigned y;
} POINT;
```
