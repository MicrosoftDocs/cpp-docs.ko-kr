---
description: '자세한 정보: 컴파일러 오류 C2432'
title: 컴파일러 오류 C2432
ms.date: 11/04/2016
f1_keywords:
- C2432
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
ms.openlocfilehash: 392108e0fd16952bc8bcf43682dc163c664171ea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190018"
---
# <a name="compiler-error-c2432"></a>컴파일러 오류 C2432

' identifier '의 16 비트 데이터에 대 한 참조가 잘못 되었습니다.

16 비트 레지스터가 인덱스 또는 기본 레지스터로 사용 됩니다. 컴파일러는 16 비트 데이터 참조를 지원 하지 않습니다. 16 비트 레지스터는 32 비트 코드를 컴파일할 때 인덱스 또는 기본 레지스터로 사용할 수 없습니다.

다음 샘플에서는 C2432를 생성 합니다.

```cpp
// C2432.cpp
// processor: x86
int main() {
   _asm mov eax, DWORD PTR [bx]   // C2432
}
```
