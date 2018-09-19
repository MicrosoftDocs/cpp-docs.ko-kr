---
title: 컴파일러 오류 C3541 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3541
dev_langs:
- C++
helpviewer_keywords:
- C3541
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a0f9cb18089bcf8ce1688cabb261f91f868da247
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021722"
---
# <a name="compiler-error-c3541"></a>컴파일러 오류 C3541

'type': 'auto'를 포함 하는 형식에 typeid를 적용할 수 없습니다

합니다 [typeid](../../windows/typeid-cpp-component-extensions.md) 있기 때문에 연산자를 지정된 된 형식에 적용할 수 없습니다는 `auto` 지정자입니다.

## <a name="example"></a>예제

다음 예제에서는 C3541를 생성합니다.

```
// C3541.cpp
// Compile with /Zc:auto
#include <typeinfo>
int main() {
    auto x = 123;
    typeid(x);    // OK
    typeid(auto); // C3541
    return 0;
}
```

## <a name="see-also"></a>참고 항목

[auto 키워드](../../cpp/auto-keyword.md)<br/>
[/Zc:auto(변수 형식 추론)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[typeid](../../windows/typeid-cpp-component-extensions.md)