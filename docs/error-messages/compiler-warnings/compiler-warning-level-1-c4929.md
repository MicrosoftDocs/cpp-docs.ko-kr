---
title: 컴파일러 경고 (수준 1) C4929 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4929
dev_langs:
- C++
helpviewer_keywords:
- C4929
ms.assetid: 95f8ab4f-4468-4caa-acd5-8f4592f03b3c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4f54758277edb03f76e67aaddb55c68224b4064
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063322"
---
# <a name="compiler-warning-level-1-c4929"></a>컴파일러 경고(수준 1) C4929

'file': typelibrary 있습니다. 'embedded_idl' 한정자를 무시합니다.

Embedded_idl 특성 [#import](../../preprocessor/hash-import-directive-cpp.md) 이므로 공용 구조체 형식 라이브러리에 있는 형식 라이브러리에 적용할 수 없습니다. 이 경고를 해결 하려면 embedded_idl를 사용 하지 마세요.

## <a name="example"></a>예제

다음 샘플 구성 요소를 정의 합니다.

```
// C4929a.cpp
// compile with: /LD /link /TLBOUT:C4929a.tlb
#include <objbase.h>
[module(name="Test")];
[public, switch_type(short)] typedef union _TD_UNION_TYPE   {
   [case(24)]
      float fM;
   [case(25)]
      double dMN;
   [default]
      int x;
} TD_UNION_TYPE;

[export, public] typedef struct _TDW_TYPE {
   [switch_is(sU)] TD_UNION_TYPE w;
      short sU;
} TD_TYPE;

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface I {
   HRESULT f(TD_TYPE*);
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct C : I {
   HRESULT f(TD_TYPE*) { return 0; }
};
```

## <a name="example"></a>예제

다음 샘플 C4929를 생성합니다.

```
// C4929b.cpp
// compile with: /c /W1
#import "C4929a.tlb" embedded_idl   // C4929
```