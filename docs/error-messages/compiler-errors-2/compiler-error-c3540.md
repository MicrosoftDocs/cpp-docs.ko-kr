---
description: '자세한 정보: 컴파일러 오류 C3540'
title: 컴파일러 오류 C3540
ms.date: 11/04/2016
f1_keywords:
- C3540
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
ms.openlocfilehash: 85106061b2631d3a392b05a50c49f24566cdd4cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97112455"
---
# <a name="compiler-error-c3540"></a>컴파일러 오류 C3540

' type ': sizeof를 ' a u t o '가 포함 된 형식에 적용할 수 없습니다.

지정 된 형식에는 지정자를 포함 하므로 [sizeof](../../cpp/sizeof-operator.md) 연산자를 적용할 수 없습니다 **`auto`** .

## <a name="example"></a>예제

다음 예에서는 C3540를 생성 합니다.

```cpp
// C3540.cpp
// Compile with /Zc:auto
int main() {
    auto x = 123;
    sizeof(x);    // OK
    sizeof(auto); // C3540
    return 0;
}
```

## <a name="see-also"></a>참조

[auto 키워드](../../cpp/auto-cpp.md)<br/>
[/Zc: auto (변수 형식 추론)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[sizeof 연산자](../../cpp/sizeof-operator.md)
