---
description: '자세한 정보: 심각한 오류 C1190'
title: 심각한 오류 C1190
ms.date: 11/04/2016
f1_keywords:
- C1190
helpviewer_keywords:
- C1190
ms.assetid: dee2266d-6c40-4f6e-91db-f01e65f8d2bc
ms.openlocfilehash: e351a04d548816999d61973276203d34745c0a75
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123606"
---
# <a name="fatal-error-c1190"></a>심각한 오류 C1190

관리되는 대상 코드에는 '/clr' 옵션을 사용해야 합니다.

CLR 구문을 사용하지만 **/clr** 을 지정하지 않았습니다.

자세한 내용은 [/clr (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)를 참조 하세요.

다음 샘플에서는 C1190을 생성합니다.

```cpp
// C1190.cpp
// compile with: /c
__gc class A {};   // C1190
ref class A {};
```
