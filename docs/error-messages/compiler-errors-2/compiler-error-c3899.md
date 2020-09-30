---
title: 컴파일러 오류 C3899
ms.date: 11/04/2016
f1_keywords:
- C3899
helpviewer_keywords:
- C3899
ms.assetid: 14e07e4a-f7a7-4309-baaa-649d69e12e23
ms.openlocfilehash: f3650d994e3102f71ab1d3598a4d1482f50b3334
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510030"
---
# <a name="compiler-error-c3899"></a>컴파일러 오류 C3899

' var ': ' class ' 클래스의 병렬 영역 내부에서는 initonly 데이터 멤버의 l-value 사용을 직접 사용할 수 없습니다.

[Initonly (c + +/cli)](../../dotnet/initonly-cpp-cli.md) 데이터 멤버는 [병렬](../../parallel/openmp/reference/openmp-directives.md#parallel) 영역에 있는 생성자의 해당 부분 내에서 초기화할 수 없습니다.  이는 컴파일러가 해당 코드의 내부 재배치를 수행 하기 때문 이며,이는 실제로 생성자의 일부가 아닙니다.

이 문제를 해결 하려면 병렬 영역 외부에서 생성자의 initonly 데이터 멤버를 초기화 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C3899를 생성 합니다.

```cpp
// C3899.cpp
// compile with: /clr /openmp
#include <omp.h>

public ref struct R {
   initonly int x;
   R() {
      x = omp_get_thread_num() + 1000;   // OK
      #pragma omp parallel num_threads(5)
      {
         // cannot assign to 'x' here
         x = omp_get_thread_num() + 1000;   // C3899
         System::Console::WriteLine("thread {0}", omp_get_thread_num());
      }
      x = omp_get_thread_num() + 1000;   // OK
   }
};

int main() {
   R^ r = gcnew R;
   System::Console::WriteLine(r->x);
}
```
