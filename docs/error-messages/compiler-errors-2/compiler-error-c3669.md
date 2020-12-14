---
description: '자세한 정보: 컴파일러 오류 C3669'
title: 컴파일러 오류 C3669
ms.date: 11/04/2016
f1_keywords:
- C3669
helpviewer_keywords:
- C3669
ms.assetid: be9c7ae4-e96f-47ab-922a-39a3537d5ca6
ms.openlocfilehash: b746c64af06178caf1006417f61c5f1e853cb67d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228952"
---
# <a name="compiler-error-c3669"></a>컴파일러 오류 C3669

' member ': 재정의 지정자 ' override '는 정적 멤버 함수 또는 생성자에서 사용할 수 없습니다.

재정의가 잘못 지정 되었습니다. 자세한 내용은 [명시적 재정의](../../extensions/explicit-overrides-cpp-component-extensions.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3669를 생성 합니다.

```cpp
// C3669.cpp
// compile with: /clr
public ref struct R {
   R() override {}   // C3669
};
```
