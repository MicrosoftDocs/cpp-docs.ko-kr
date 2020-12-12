---
description: '자세히 알아보기: 방법: 내부 포인터 및 네이티브 포인터를 사용 하 여 함수 오버 로드 (c + +/CLI)'
title: '방법: 내부 포인터 및 네이티브 포인터를 사용하여 함수 오버로드(C++/CLI)'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- Functions with interior and native pointers, overloading
ms.assetid: d70df625-4aad-457c-84f5-70a0a290cc1f
ms.openlocfilehash: f68861b7140ed3ae7fac84bc9a197f68ddd9b72d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119150"
---
# <a name="how-to-overload-functions-with-interior-pointers-and-native-pointers-ccli"></a>방법: 내부 포인터 및 네이티브 포인터를 사용하여 함수 오버로드(C++/CLI)

매개 변수 형식이 내부 포인터인지, 네이티브 포인터인지에 따라 함수를 오버로드할 수 있습니다.

> [!IMPORTANT]
> 이 언어 기능은 `/clr` 컴파일러 옵션에서 지원하지만 `/ZW` 컴파일러 옵션에서는 지원하지 않습니다.

## <a name="example"></a>예제

### <a name="code"></a>코드

```cpp
// interior_ptr_overload.cpp
// compile with: /clr
using namespace System;

// C++ class
struct S {
   int i;
};

// managed class
ref struct G {
   int i;
};

// can update unmanaged storage
void f( int* pi ) {
   *pi = 10;
   Console::WriteLine("in f( int* pi )");
}

// can update managed storage
void f( interior_ptr<int> pi ) {
   *pi = 10;
   Console::WriteLine("in f( interior_ptr<int> pi )");
}

int main() {
   S *pS = new S;   // C++ heap
   G ^pG = gcnew G;   // common language runtime heap
   f( &pS->i );
   f( &pG->i );
};
```

```Output
in f( int* pi )
in f( interior_ptr<int> pi )
```

## <a name="see-also"></a>참조

[interior_ptr (c + +/CLI)](interior-ptr-cpp-cli.md)
