---
description: '자세한 정보: 컴파일러 오류 C2141'
title: 컴파일러 오류 C2141
ms.date: 11/04/2016
f1_keywords:
- C2141
helpviewer_keywords:
- C2141
ms.assetid: 10cf770f-0500-4220-ac90-a863b7ea5fe6
ms.openlocfilehash: ea80cd02b3a7ec213b7b6d0eb3c0c1d4d94298b8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270942"
---
# <a name="compiler-error-c2141"></a>컴파일러 오류 C2141

배열 크기 오버플로

배열이 2GB 제한을 초과 합니다. 배열의 크기를 줄입니다.

## <a name="example"></a>예제

다음 샘플에서는 C2141를 생성 합니다.

```cpp
// C2141.cpp
// processor: IPF
class A {
   short m_n;
};

int main()
{
   A* pA = (A*)(-1);
   pA = new A[0x8000000000000001];   // C2141

   A* pA2 = (A*)(-1);
   pA2 = new A[0x80000000000000F];   // OK
}
```
