---
description: '자세한 정보: 컴파일러 오류 C3050'
title: 컴파일러 오류 C3050
ms.date: 11/04/2016
f1_keywords:
- C3050
helpviewer_keywords:
- C3050
ms.assetid: ee090a0b-29cc-4215-a2f9-d82af79b8e82
ms.openlocfilehash: 354efe0ba8445042571d76cfeeb41e98fae96256
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269668"
---
# <a name="compiler-error-c3050"></a>컴파일러 오류 C3050

'type1': ref 클래스는 'type1'에서 상속될 수 없습니다.

`System::ValueType` 이 참조 형식에 대한 기본 클래스가 될 수 없습니다.

다음 샘플에서는 C3050을 생성합니다.

```cpp
// C3050.cpp
// compile with: /clr /LD
ref struct X : System::ValueType {};   // C3050
ref struct Y {};   // OK
```
