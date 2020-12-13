---
description: '자세한 정보: 컴파일러 오류 C3293'
title: 컴파일러 오류 C3293
ms.date: 07/21/2017
f1_keywords:
- C3293
helpviewer_keywords:
- C3293
ms.assetid: b772cf98-52e0-4e24-be23-1f5d87d999ac
ms.openlocfilehash: 5ba4256997eed12d3a380d5f3a4d1876da75fb8c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144640"
---
# <a name="compiler-error-c3293"></a>컴파일러 오류 C3293

'accessor': 'default'를 사용하여 'type' 클래스의 기본 속성(인덱서)에 액세스하세요.

인덱싱된 속성에 잘못 액세스했습니다.  자세한 내용은 [방법: c + +/cli에서 속성 사용을](../../dotnet/how-to-use-properties-in-cpp-cli.md) 참조 하세요.

**Visual studio 2017 이상**: visual studio 2015이 하 버전에서는 경우에 따라 컴파일러는 기본 속성을 기본 misidentified 합니다. 속성에 액세스하는 데 식별자 "default"를 사용하여 문제를 해결할 수 있었습니다. default가 C++11에서 키워드로 도입된 이후 해결 방법 자체가 문제가 되었습니다. 따라서 Visual Studio 2017에서는 해결 방법이 필요했던 버그가 수정되었고 이제 컴파일러는 "default"가 클래스에 대한 기본 속성에 액세스하는 데 사용될 경우 오류를 발생시킵니다.

## <a name="example"></a>예제

다음 샘플에서는 Visual Studio 2015 및 이전 버전에서 C3293를 생성 합니다.

```cpp
// C3293.cpp
// compile with: /clr /c
using namespace System;
ref class IndexerClass {
public:
   // default indexer
   property int default[int] {
      int get(int index) { return 0; }
      void set(int index, int value) {}
   }
};

int main() {
   IndexerClass ^ ic = gcnew IndexerClass;
   ic->Item[0] = 21;   // C3293 in VS2015 OK in VS2017
   ic->default[0] = 21;   // OK in VS2015 and earlier

   String ^s = "Hello";
   wchar_t wc = s->Chars[0];   // C3293 in VS2015 OK in VS2017
   wchar_t wc2 = s->default[0];   // OK in VS2015 and earlier
   Console::WriteLine(wc2);
}
```
