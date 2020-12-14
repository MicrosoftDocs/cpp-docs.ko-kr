---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4336'
title: 컴파일러 경고(수준 4) C4336
ms.date: 11/04/2016
f1_keywords:
- C4336
helpviewer_keywords:
- C4336
ms.assetid: 93f199dd-d6dd-42c0-82d8-c12d101a7235
ms.openlocfilehash: d41ca5584864327b3012e79af97f2857e3f93d42
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257721"
---
# <a name="compiler-warning-level-4-c4336"></a>컴파일러 경고(수준 4) C4336

' type_lib2 '를 가져오기 전에 상호 참조 된 형식 라이브러리 ' type_lib1 ' 가져오기

[#Import](../../preprocessor/hash-import-directive-cpp.md) 지시어를 사용 하 여 형식 라이브러리를 참조 했습니다. 그러나 형식 라이브러리에는에서 참조 되지 않은 다른 형식 라이브러리에 대 한 참조가 포함 되어 `#import` 있습니다. 이 다른 .tlb 파일은 컴파일러에 의해 발견 되었습니다.

다음 두 파일 (midl.exe로 컴파일)에서 만든 디스크에 두 개의 형식 라이브러리가 지정 됩니다.

```
// c4336a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library c4336aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12c")]
   enum E_C4336
   {
      one, two, three
   };
};
```

두 번째 형식 라이브러리는 다음과 같습니다.

```
// c4336b.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
library C4336bLib
{
   importlib ("c4336a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
   struct S_C4336
   {
      enum E_C4336 e;
   };
};
```

다음 샘플에서는 C4336를 생성 합니다.

```cpp
// C4336.cpp
// compile with: /W4 /LD
// #import "C4336a.tlb"
#import "C4336b.tlb"   // C4336, uncomment previous line to resolve
```
