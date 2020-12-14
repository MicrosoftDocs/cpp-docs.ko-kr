---
description: '자세한 정보: 컴파일러 오류 C3831'
title: 컴파일러 오류 C3831
ms.date: 11/04/2016
f1_keywords:
- C3831
helpviewer_keywords:
- C3831
ms.assetid: a125d8dc-b75a-4ea0-b6c7-fe7b119dba25
ms.openlocfilehash: ba3d1e7f6dfc2670307e510ee6eb13fa6277bc1c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311814"
---
# <a name="compiler-error-c3831"></a>컴파일러 오류 C3831

' member ': ' class '에 고정 된 데이터 멤버 또는 고정 포인터를 반환 하는 멤버 함수를 사용할 수 없습니다.

[pin_ptr (c + +/cli)](../../extensions/pin-ptr-cpp-cli.md) 가 잘못 사용 되었습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3831를 생성 합니다.

```cpp
// C3831a.cpp
// compile with: /clr
ref class Y
{
public:
   int i;
};

ref class X
{
   pin_ptr<int> mbr_Y;   // C3831
   int^ mbr_Y2;   // OK
};

int main() {
   Y y;
   pin_ptr<int> p = &y.i;
}
```
