---
description: '자세한 정보: 컴파일러 경고 C4439'
title: 컴파일러 경고 C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: 123f42ca495faeccc995dc1ac87572180d1dce70
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180749"
---
# <a name="compiler-warning-c4439"></a>컴파일러 경고 C4439

' function ': 시그니처에 관리 되는 형식이 있는 함수 정의에는 __clrcall 호출 규칙이 있어야 합니다.

컴파일러는 호출 규칙을로 암시적으로 바꿉니다 [`__clrcall`](../../cpp/clrcall.md) . 이 경고를 해결 하려면 **`__cdecl`** 또는 호출 규칙을 제거 합니다 **`__stdcall`** .

C4439는 항상 오류로 실행 됩니다. 또는를 사용 하 여이 경고를 해제할 수 있습니다 `#pragma warning` **`/wd`** . 자세한 내용은 [경고](../../preprocessor/warning.md) 또는 [/w,/W0,/W1,/W2,/W3,](../../build/reference/compiler-option-warning-level.md) /W4,/W1,/W2,/W3,/W4,/Wall,/wd,/WE,/Wo,/Wv,/wx (경고 수준)를 참조 하십시오.

## <a name="example"></a>예제

다음 샘플에서는 C4439를 생성 합니다.

```cpp
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```
