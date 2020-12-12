---
description: '자세한 정보: 컴파일러 오류 C2431'
title: 컴파일러 오류 C2431
ms.date: 11/04/2016
f1_keywords:
- C2431
helpviewer_keywords:
- C2431
ms.assetid: 88a5b648-c89f-47d1-a20e-63231ab4f0f7
ms.openlocfilehash: af575403408454916b65bfaf6549f4b3e9fad624
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190044"
---
# <a name="compiler-error-c2431"></a>컴파일러 오류 C2431

' identifier '의 인덱스 레지스터가 잘못 되었습니다.

ESP 레지스터는 확장 되거나 인덱스 및 기본 레지스터로 모두 사용 됩니다. X86 프로세서의 SIB 인코딩은 둘 중 하나를 허용 하지 않습니다.

다음 샘플에서는 C2431를 생성 합니다.

```cpp
// C2431.cpp
// processor: x86
int main() {
   _asm mov ax, [ESI + 2*ESP]   // C2431
   _asm mov ax, [esp + esp]   // C2431
}
```
