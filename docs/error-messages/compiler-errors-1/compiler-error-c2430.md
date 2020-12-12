---
description: '자세한 정보: 컴파일러 오류 C2430'
title: 컴파일러 오류 C2430
ms.date: 11/04/2016
f1_keywords:
- C2430
helpviewer_keywords:
- C2430
ms.assetid: 07c20f76-63e1-4d22-b2a9-98b0d45c5cac
ms.openlocfilehash: 9f953ee78b6e4b82ce0ebd4a6621f0f06abadadb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190057"
---
# <a name="compiler-error-c2430"></a>컴파일러 오류 C2430

' identifier '에 인덱스 레지스터가 두 개 이상 있습니다.

둘 이상의 레지스터가 확장 됩니다. 컴파일러는 크기 조정 된 인덱싱을 지원 하지만 하나의 레지스터를 확장할 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C2430를 생성 합니다.

```cpp
// C2430.cpp
// processor: x86
int main() {
   _asm mov eax, [ebx*2+ecx*4] // C2430
}
```
