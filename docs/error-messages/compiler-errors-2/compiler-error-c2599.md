---
description: '자세한 정보: 컴파일러 오류 C2599'
title: 컴파일러 오류 C2599
ms.date: 11/04/2016
f1_keywords:
- C2599
helpviewer_keywords:
- C2599
ms.assetid: 88515f36-7589-47e2-862e-0de8b18d6668
ms.openlocfilehash: e1365ee2570d4af524f7e4dbd36a411916efb9c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97312048"
---
# <a name="compiler-error-c2599"></a>컴파일러 오류 C2599

' enum ': 열거형 형식의 전방 선언을 사용할 수 없습니다.

컴파일러가 더 이상 관리 되는 열거형의 전방 선언을 지원 하지 않습니다.

[/Za](../../build/reference/za-ze-disable-language-extensions.md)에서 열거형 형식의 전방 선언을 사용할 수 없습니다.

다음 샘플에서는 C2599를 생성 합니다.

```cpp
// C2599.cpp
// compile with: /clr /c
enum class Status;   // C2599

enum class Status2 { stop2, hold2, go2};

ref struct MyStruct {
   // Delete the following line to resolve.
   Status m_status;

   Status2 m_status2;   // OK
};

enum class Status { stop, hold, go };
```
