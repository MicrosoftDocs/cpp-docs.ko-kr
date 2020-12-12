---
description: '자세한 정보: 컴파일러 오류 C2904'
title: 컴파일러 오류 C2904
ms.date: 11/04/2016
f1_keywords:
- C2904
helpviewer_keywords:
- C2904
ms.assetid: d5802f2e-d3fc-473d-aa04-36957b4eaca5
ms.openlocfilehash: f49ff355a69fd0487e10de088e9a676f4b6981af
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270695"
---
# <a name="compiler-error-c2904"></a>컴파일러 오류 C2904

'identifier': 이름이 현재 범위의 템플릿으로 이미 사용되었습니다.

코드 이름이 중복되지 않았는지 확인합니다.

다음 샘플에서는 C2904를 생성합니다.

```cpp
// C2904.cpp
// compile with: /c
void X();  // X is declared as a function
template<class T> class X{};  // C2904
```
