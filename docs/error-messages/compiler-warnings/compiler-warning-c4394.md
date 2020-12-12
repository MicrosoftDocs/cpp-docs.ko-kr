---
description: '자세한 정보: 컴파일러 경고 C4394'
title: 컴파일러 경고 C4394
ms.date: 11/04/2016
f1_keywords:
- C4394
helpviewer_keywords:
- C4394
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
ms.openlocfilehash: 8a732e4cc1b3454a0dd602cd36b9ae8b959a8118
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180762"
---
# <a name="compiler-warning-c4394"></a>컴파일러 경고 C4394

' function ': appdomain 별 기호는 __declspec (dllexport)로 표시 되어서는 안 됩니다.

[Appdomain](../../cpp/appdomain.md) 한정자로 표시 된 함수는 **`__declspec`** MSIL로 컴파일되고 (native가 아님) 관리 되는 함수에 대해 테이블 내보내기 ([내보내기](../../windows/attributes/export.md) **`__declspec`** 한정자)가 지원 되지 않습니다.

공용 액세스 가능성을 갖도록 관리되는 함수를 선언할 수 있습니다. 자세한 내용은 [형식 표시](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) 유형 및 [멤버 표시](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility)유형을 참조 하세요.

C4394는 항상 오류로 실행 됩니다.  또는/wd를 사용 하 여이 경고를 해제할 수 있습니다 `#pragma warning` . 자세한 내용은 [경고](../../preprocessor/warning.md) 또는 [/W,/W0,/W1,/W2,](../../build/reference/compiler-option-warning-level.md) /W3,/W4,/W1,/W2,/W3,/W4,/Wall,/wd,/we,/wo,/Wv,/wx (경고 수준)를 참조 하십시오. 

## <a name="example"></a>예제

다음 샘플에서는 C4394를 생성 합니다.

```cpp
// C4394.cpp
// compile with: /clr /c
__declspec(dllexport) __declspec(appdomain) int g1 = 0;   // C4394
__declspec(dllexport) int g2 = 0;   // OK
```
