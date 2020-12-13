---
description: '자세한 정보: 컴파일러 경고 (수준 3) C4414'
title: 컴파일러 경고(수준 3) C4414
ms.date: 11/04/2016
f1_keywords:
- C4414
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
ms.openlocfilehash: c753852d40a044e99b91aa8a5976811aab52c5ab
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177174"
---
# <a name="compiler-warning-level-3-c4414"></a>컴파일러 경고(수준 3) C4414

' function ': 함수로의 short 점프는 near로 변환 됩니다.

짧은 점프는 명령에서 제한 된 범위 내의 주소로 분기 하는 압축 명령을 생성 합니다. 명령에는 점프와 대상 주소 간의 거리 (함수 정의)를 나타내는 짧은 오프셋이 포함 됩니다. 연결 중에 함수를 이동 하거나 링크 타임 최적화를 적용 하 여 함수를 짧은 오프셋에서 도달할 수 있는 범위 밖으로 이동 시킬 수 있습니다. 컴파일러는 이동에 대 한 특수 레코드를 생성 해야 합니다 .이 경우 jmp 명령이 가까이 나 멀리 있어야 합니다. 컴파일러가 변환을 수행 했습니다.

예를 들어 다음 코드는 C4414을 생성 합니다.

```cpp
// C4414.cpp
// compile with: /W3 /c
// processor: x86
int DoParityEven();
int DoParityOdd();
unsigned char global;
int __declspec(naked) DoParityEither()
{
   __asm
   {
      test global,0
      jpe SHORT DoParityEven  // C4414
      jmp SHORT DoParityOdd   // C4414
   }
}
```
