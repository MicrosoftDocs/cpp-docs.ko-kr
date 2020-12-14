---
description: '자세한 정보: 컴파일러 오류 C3510'
title: 컴파일러 오류 C3510
ms.date: 11/04/2016
f1_keywords:
- C3510
helpviewer_keywords:
- C3510
ms.assetid: c48387bc-0300-4a4d-97f7-3fb90f82a451
ms.openlocfilehash: 97727f22e94993cff051c57b5692e9a14c9ab930
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315428"
---
# <a name="compiler-error-c3510"></a>컴파일러 오류 C3510

' type_lib ' 종속 형식 라이브러리를 찾을 수 없습니다.

[no_registry](../../preprocessor/no-registry.md) 및 [auto_search](../../preprocessor/auto-search.md) 에 전달 `#import` 되었지만 컴파일러가 참조 된 형식 라이브러리를 찾을 수 없습니다.

이 오류를 해결 하려면 모든 형식 라이브러리와 참조 형식 라이브러리를 컴파일러에서 사용할 수 있는지 확인 합니다.

다음 샘플에서는 C3510를 생성 합니다.

다음 두 가지 형식 라이브러리가 빌드 되었으며 해당 경로에서 C3510a이 삭제 되었거나 삭제 되지 않았다고 가정 합니다.

```
// C3510a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library C3510aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12c")]
   enum E_C3510
   {
      one, two, three
   };
};
```

그런 다음 두 번째 형식 라이브러리에 대 한 소스 코드를 수행 합니다.

```
// C3510b.idl
// post-build command: del /f C3510a.tlb
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
library C3510bLib
{
   importlib ("C3510a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
   struct S_C3510 {
      enum E_C3510 e;
   };
};
```

클라이언트 코드는 다음과 같습니다.

```cpp
// C3510.cpp
#import "c3510b.tlb" no_registry auto_search   // C3510
int main() {
   C3510aLib::S_C4336 ccc;
}
```
