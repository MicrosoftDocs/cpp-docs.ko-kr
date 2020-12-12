---
description: '자세한 정보: 컴파일러 오류 C3268'
title: 컴파일러 오류 C3268
ms.date: 11/04/2016
f1_keywords:
- C3268
helpviewer_keywords:
- C3268
ms.assetid: d74a630c-daea-4e29-9759-83efef7fb184
ms.openlocfilehash: 405977afe5a58545dd5e8b0d54cb08f431935191
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223323"
---
# <a name="compiler-error-c3268"></a>컴파일러 오류 C3268

> '*function*': 제네릭 함수 또는 제네릭 클래스의 멤버 함수에는 가변 매개 변수 목록을 사용할 수 없습니다.

## <a name="remarks"></a>설명

**/Clr: pure** 및 **/clr: safe** 컴파일러 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

자세한 내용은 [제네릭](../../extensions/generics-cpp-component-extensions.md) 을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3268을 생성합니다.

```cpp
// C3268.cpp
// compile with: /clr:pure /c
generic <class ItemType>
void Test(ItemType item, ...) {}   // C3268
// try the following line instead
// void Test(ItemType item) {}

generic <class ItemType2>
ref struct MyStruct { void Test(...){} };   // C3268
// try the following line instead
// ref struct MyStruct { void Test2(){} };   // OK
```
