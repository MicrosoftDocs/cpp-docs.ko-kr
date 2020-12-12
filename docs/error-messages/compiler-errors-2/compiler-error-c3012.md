---
description: '자세한 정보: 컴파일러 오류 C3012'
title: 컴파일러 오류 C3012
ms.date: 11/04/2016
f1_keywords:
- C3012
helpviewer_keywords:
- C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
ms.openlocfilehash: fff986a984acb62f770d02ff2b7b08c40e8511e3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286009"
---
# <a name="compiler-error-c3012"></a>컴파일러 오류 C3012

> '*내장* 함수 ': 병렬 영역 내부에서는 직접 내장 함수를 사용할 수 없습니다.

[컴파일러 내장](../../intrinsics/compiler-intrinsics.md) 함수는 `omp parallel` 지역에서 사용할 수 없습니다. 이 문제를 해결 하려면 내장 함수를 지역 외부로 이동 하거나 비 내장 함수로 바꿉니다.

## <a name="example"></a>예제

다음 샘플에서는 C3012를 생성 하 고이를 해결 하는 한 가지 방법을 보여 줍니다.

```cpp
// C3012.cpp
// compile with: /openmp
#ifdef __cplusplus
extern "C" {
#endif
void* _ReturnAddress();
#ifdef __cplusplus
}
#endif

int main()
{
   #pragma omp parallel
   {
      _ReturnAddress();   // C3012
   }
   _ReturnAddress();      // OK
}
```
