---
description: '자세한 정보: 컴파일러 오류 C3895'
title: 컴파일러 오류 C3895
ms.date: 11/04/2016
f1_keywords:
- C3895
helpviewer_keywords:
- C3895
ms.assetid: 771b9fe5-d6d4-4297-bf57-e2f857722155
ms.openlocfilehash: ae963eb89ee8f0cefc9092e9d3b16aa40885e63c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315116"
---
# <a name="compiler-error-c3895"></a>컴파일러 오류 C3895

' var ': 형식 데이터 멤버는 ' volatile ' 일 수 없습니다.

[리터럴](../../extensions/literal-cpp-component-extensions.md) 또는 [initonly](../../dotnet/initonly-cpp-cli.md)와 같은 특정 종류의 데이터 멤버는 [volatile](../../cpp/volatile-cpp.md)일 수 없습니다.

다음 샘플에서는 C3895를 생성 합니다.

```cpp
// C3895.cpp
// compile with: /clr
ref struct Y1 {
   initonly
   volatile int data_var2;   // C3895
};
```
