---
description: '자세한 정보: 컴파일러 오류 C3622'
title: 컴파일러 오류 C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: 19c599fced524001f360a4ad462a9dbebbfb2fa3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223037"
---
# <a name="compiler-error-c3622"></a>컴파일러 오류 C3622

' class ': ' keyword '로 선언 된 클래스를 인스턴스화할 수 없습니다.

[Abstract](../../extensions/abstract-cpp-component-extensions.md)로 표시 된 클래스를 인스턴스화하려고 했습니다. 로 표시 된 클래스는 **`abstract`** 기본 클래스가 될 수 있지만 인스턴스화할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3622를 생성 합니다.

```cpp
// C3622.cpp
// compile with: /clr
ref class a abstract {};

int main() {
   a aa;   // C3622
}
```
