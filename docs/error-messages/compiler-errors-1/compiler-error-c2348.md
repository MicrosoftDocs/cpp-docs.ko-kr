---
description: '자세한 정보: 컴파일러 오류 C2348'
title: 컴파일러 오류 C2348
ms.date: 11/04/2016
f1_keywords:
- C2348
helpviewer_keywords:
- C2348
ms.assetid: 4c4d701f-ccf1-46fe-9ddb-3f341684f269
ms.openlocfilehash: 829bd94c8fe78280b8b49b74f218e2143dda4335
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298359"
---
# <a name="compiler-error-c2348"></a>컴파일러 오류 C2348

' type name ': C 스타일 집합체가 아니므로 포함 IDL에서 내보낼 수 없습니다.

내보내기 특성을 사용 하 여을 **`struct`** .idl 파일에 [](../../windows/attributes/export.md) 추가 하려면에 데이터만 **`struct`** 포함 되어야 합니다.

다음 샘플에서는 C2348를 생성 합니다.

```cpp
// C2348.cpp
// C2348 error expected
[ module(name="SimpleMidlTest") ];

[export]
struct Point {
   // Delete the following two lines to resolve.
   Point() : m_i(0), m_j(0) {}
   Point(int i, int j) : m_i(i), m_j(j) {}

   int m_i;
   int m_j;
};
```
