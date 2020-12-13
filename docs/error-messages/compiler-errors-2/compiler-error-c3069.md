---
description: '자세한 정보: 컴파일러 오류 C3069'
title: 컴파일러 오류 C3069
ms.date: 11/04/2016
f1_keywords:
- C3069
helpviewer_keywords:
- C3069
ms.assetid: ca94291b-2bb4-4e3f-9acf-534234b83513
ms.openlocfilehash: cc56ded4f14e137b9f5bf28681fb319a650f363a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341141"
---
# <a name="compiler-error-c3069"></a>컴파일러 오류 C3069

'operator': 열거형 형식에 사용할 수 없습니다.

CLR 열거형에 대해서는 연산자가 지원되지 않습니다.  자세한 내용은 [방법: c + +/cli에서 열거형 정의 및 사용](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3069를 생성합니다.

```cpp
// C3069.cpp
// compile with: /clr
enum struct E { e1 };
enum F { f1 };

int main() {
   E e = E::e1;
   bool tf;
   tf = !e;   // C3069

   // supported for native enums
   F f = f1;
   tf = !f;
}
```
