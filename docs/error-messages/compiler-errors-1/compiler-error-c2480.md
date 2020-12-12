---
description: '자세한 정보: 컴파일러 오류 C2480'
title: 컴파일러 오류 C2480
ms.date: 11/04/2016
f1_keywords:
- C2480
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
ms.openlocfilehash: 0c7f73b7e1aa205d38577602b93907309935b216
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316546"
---
# <a name="compiler-error-c2480"></a>컴파일러 오류 C2480

' identifier ': ' thread '는 정적 범위의 데이터 항목에만 사용할 수 있습니다.

`thread`자동 변수, 비정적 데이터 멤버, 함수 매개 변수 또는 함수 선언 또는 정의에는 특성을 사용할 수 없습니다.

`thread`전역 변수, 정적 데이터 멤버 및 지역 정적 변수에만 특성을 사용 합니다.

다음 샘플에서는 C2480를 생성 합니다.

```cpp
// C2480.cpp
// compile with: /c
__declspec( thread ) void func();   // C2480
__declspec( thread ) static int i;   // OK
```
