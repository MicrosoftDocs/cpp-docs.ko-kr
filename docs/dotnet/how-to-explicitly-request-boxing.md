---
title: '방법: 명시적으로 Boxing 요청 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- boxing, explicitly requesting
ms.assetid: 1359e6e5-162d-4f5d-9b6a-1690d93df3ee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 14155973da6c733fba375300fd3e29ca3a8762ce
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378998"
---
# <a name="how-to-explicitly-request-boxing"></a>방법: 명시적으로 boxing 요청

형식의 변수에 변수를 할당 하 여 명시적으로 boxing 요청 수 `Object`입니다.

## <a name="example"></a>예제

```
// vcmcppv2_explicit_boxing3.cpp
// compile with: /clr
using namespace System;

void f(int i) {
   Console::WriteLine("f(int i)");
}

void f(Object ^o) {
   Console::WriteLine("f(Object^ o)");
}

int main() {
   int i = 5;
   Object ^ O = i;   // forces i to be boxed
   f(i);
   f(O);
   f( (Object^)i );  // boxes i
}
```

```Output
f(int i)
f(Object^ o)
f(Object^ o)
```

## <a name="see-also"></a>참고 항목

[Boxing](../windows/boxing-cpp-component-extensions.md)