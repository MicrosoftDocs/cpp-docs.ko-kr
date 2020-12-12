---
description: '자세한 정보: 컴파일러 오류 C2842'
title: 컴파일러 오류 C2842
ms.date: 11/04/2016
f1_keywords:
- C2842
helpviewer_keywords:
- C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
ms.openlocfilehash: f086c6c5fcfa451f320d96470615e4f5f4d5674a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119985"
---
# <a name="compiler-error-c2842"></a>컴파일러 오류 C2842

> '*class*': 관리 되는 형식 또는 WinRT 형식은 고유한 ' operator new ' 또는 ' operator delete '를 정의할 수 없습니다.

## <a name="remarks"></a>설명

사용자 고유의 **operator new** 또는 **operator delete** 를 정의 하 여 네이티브 힙의 메모리 할당을 관리할 수 있습니다. 그러나 참조 클래스는 관리되는 힙에만 할당되기 때문에 이러한 연산자를 정의할 수 없습니다.

자세한 내용은 [사용자 정의 연산자 (c + +/cli)](../../dotnet/user-defined-operators-cpp-cli.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C2842 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C2842.cpp
// compile with: /clr /c
ref class G {
   void* operator new( size_t nSize );   // C2842
};
```
