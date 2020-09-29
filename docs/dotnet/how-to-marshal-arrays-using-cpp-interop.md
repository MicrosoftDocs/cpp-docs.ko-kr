---
title: '방법: C++ Interop를 사용하여 배열 마샬링'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [C++], marshaling
- marshaling [C++], arrays
- interop [C++], arrays
- C++ Interop, arrays
- data marshaling [C++], arrays
ms.assetid: c2b37ab1-8acf-4855-ad3c-7d2864826b14
ms.openlocfilehash: 0ccf71d40db0bc6989620d2ca126ce74311805da
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413829"
---
# <a name="how-to-marshal-arrays-using-c-interop"></a>방법: C++ Interop를 사용하여 배열 마샬링

이 항목에서는 Visual C++ 상호 운용성의 한 패싯을 보여 줍니다. 자세한 내용은 [c + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)을 참조 하세요.

다음 코드 예제에서는 관리 되는 관리 [되지 않는](../preprocessor/managed-unmanaged.md) #pragma 지시문을 사용 하 여 동일한 파일에서 관리 되는 함수 및 관리 되지 않는 함수를 구현 하지만 이러한 함수는 별도의 파일에 정의 된 경우와 동일한 방식으로 상호 운용 됩니다 관리 되지 않는 함수만 포함 하는 파일은 [/clr (공용 언어 런타임 컴파일)](../build/reference/clr-common-language-runtime-compilation.md)을 사용 하 여 컴파일할 필요가 없습니다.

## <a name="example-pass-managed-array-to-unmanaged-function"></a>예: 관리 되는 배열을 관리 되지 않는 함수에 전달

다음 예제에서는 관리 되는 배열을 관리 되지 않는 함수에 전달 하는 방법을 보여 줍니다. 관리 되는 함수는 관리 되지 않는 함수를 호출 하기 전에 [pin_ptr (c + +/cli)](../extensions/pin-ptr-cpp-cli.md) 를 사용 하 여 배열의 가비지 수집을 표시 하지 않습니다. 관리 되지 않는 함수에 GC 힙에 고정 된 포인터를 제공 하면 배열의 복사본을 만드는 오버 헤드를 피할 수 있습니다. 관리 되지 않는 함수가 GC 힙 메모리에 액세스 함을 보여 주기 위해 배열의 내용을 수정 하 고 관리 되는 함수가 제어를 다시 시작할 때 변경 내용이 반영 됩니다.

```cpp
// PassArray1.cpp
// compile with: /clr
#ifndef _CRT_RAND_S
#define _CRT_RAND_S
#endif

#include <iostream>
#include <stdlib.h>
using namespace std;

using namespace System;

#pragma unmanaged

void TakesAnArray(int* a, int c) {
   cout << "(unmanaged) array received:\n";
   for (int i=0; i<c; i++)
      cout << "a[" << i << "] = " << a[i] << "\n";

   unsigned int number;
   errno_t err;

   cout << "(unmanaged) modifying array contents...\n";
   for (int i=0; i<c; i++) {
      err = rand_s( &number );
      if ( err == 0 )
         a[i] = number % 100;
   }
}

#pragma managed

int main() {
   array<int>^ nums = gcnew array<int>(5);

   nums[0] = 0;
   nums[1] = 1;
   nums[2] = 2;
   nums[3] = 3;
   nums[4] = 4;

   Console::WriteLine("(managed) array created:");
   for (int i=0; i<5; i++)
      Console::WriteLine("a[{0}] = {1}", i, nums[i]);

   pin_ptr<int> pp = &nums[0];
   TakesAnArray(pp, 5);

   Console::WriteLine("(managed) contents:");
   for (int i=0; i<5; i++)
      Console::WriteLine("a[{0}] = {1}", i, nums[i]);
}
```

## <a name="example-pass-unmanaged-array-to-managed-function"></a>예: 관리 되지 않는 배열을 관리 되는 함수에 전달

다음 예제에서는 관리 되는 함수에 관리 되지 않는 배열을 전달 하는 방법을 보여 줍니다. 관리 되는 함수는 관리 되는 배열을 만들고 배열 콘텐츠를 복사 하는 것과는 반대로 배열 메모리에 직접 액세스 하 여 관리 되는 함수가 제어를 다시 설정할 때 관리 되지 않는 함수에 반영 되도록 합니다.

```cpp
// PassArray2.cpp
// compile with: /clr
#include <iostream>
using namespace std;

using namespace System;

#pragma managed

void ManagedTakesAnArray(int* a, int c) {
   Console::WriteLine("(managed) array received:");
   for (int i=0; i<c; i++)
      Console::WriteLine("a[{0}] = {1}", i, a[i]);

   cout << "(managed) modifying array contents...\n";
   Random^ r = gcnew Random(DateTime::Now.Second);
   for (int i=0; i<c; i++)
      a[i] = r->Next(100);
}

#pragma unmanaged

void NativeFunc() {
   int nums[5] = { 0, 1, 2, 3, 4 };

   printf_s("(unmanaged) array created:\n");
   for (int i=0; i<5; i++)
      printf_s("a[%d] = %d\n", i, nums[i]);

   ManagedTakesAnArray(nums, 5);

   printf_s("(ummanaged) contents:\n");
   for (int i=0; i<5; i++)
      printf_s("a[%d] = %d\n", i, nums[i]);
}

#pragma managed

int main() {
   NativeFunc();
}
```

## <a name="see-also"></a>참고 항목

[C + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
