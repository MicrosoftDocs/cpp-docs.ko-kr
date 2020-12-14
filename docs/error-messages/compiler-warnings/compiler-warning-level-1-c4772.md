---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4772'
title: 컴파일러 경고(수준 1) C4772
ms.date: 11/04/2016
f1_keywords:
- C4772
helpviewer_keywords:
- C4772
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
ms.openlocfilehash: 41fcbf3074cb1e51e06ba21a01a27eaf8ded1b31
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228445"
---
# <a name="compiler-warning-level-1-c4772"></a>컴파일러 경고(수준 1) C4772

> \#가져오기는 누락 된 형식 라이브러리에서 형식을 참조 합니다. '*누락 된 형식*'이 자리 표시자로 사용 되었습니다.

[#Import](../../preprocessor/hash-import-directive-cpp.md) 지시어를 사용 하 여 형식 라이브러리를 참조 했습니다. 그러나 형식 라이브러리에는에서 참조 되지 않은 다른 형식 라이브러리에 대 한 참조가 포함 되어 `#import` 있습니다. 이 다른 .tlb 파일을 컴파일러에서 찾지 못했습니다.

[/I (추가 포함 디렉터리)](../../build/reference/i-additional-include-directories.md) 컴파일러 옵션을 사용 하 여 해당 디렉터리를 지정 하는 경우 컴파일러는 다른 디렉터리에서 형식 라이브러리를 찾을 수 없습니다. 컴파일러가 다른 디렉터리에서 형식 라이브러리를 찾도록 하려면 해당 디렉터리를 PATH 환경 변수에 추가 합니다.

기본적으로이 경고는 오류로 실행 됩니다. C4772는/W0.를 사용 하 여 숨길 수 없습니다.

## <a name="example"></a>예제

C4772를 재현 하는 데 필요한 첫 번째 형식 라이브러리입니다.

```IDL
// c4772a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library C4772aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c100")]
   enum E_C4772a
   {
      one, two, three
   };
};
```

C4772를 재현 하는 데 필요한 두 번째 형식 라이브러리입니다.

```IDL
// c4772b.idl
// post-build command: del /f C4772a.tlb
// C4772a.tlb is available when c4772b.tlb is built
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
library C4772bLib
{
   importlib ("c4772a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
   struct S_C4772b
   {
      enum E_C4772a e;
   };
};
```

다음 샘플에서는 C4772를 생성 합니다.

```cpp
// C4772.cpp
// assumes that C4772a.tlb is not available to the compiler
// #import "C4772a.tlb"
#import "C4772b.tlb"   // C4772 uncomment previous line to resolve
                       // and make sure c4772a.tlb is on disk
```
