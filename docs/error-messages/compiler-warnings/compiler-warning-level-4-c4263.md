---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4263'
title: 컴파일러 경고(수준 4) C4263
ms.date: 11/04/2016
f1_keywords:
- C4263
helpviewer_keywords:
- C4263
ms.assetid: daabb05d-ab56-460f-ab6c-c74d222ef649
ms.openlocfilehash: 7b7eb7fdf8e66ab5d09c8dc0f9511d3c88162084
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339146"
---
# <a name="compiler-warning-level-4-c4263"></a>컴파일러 경고(수준 4) C4263

' function ': 멤버 함수가 기본 클래스 가상 멤버 함수를 재정의 하지 않습니다.

클래스 함수 정의의 이름이 기본 클래스의 가상 함수와 같지만 인수의 수 나 형식이 다릅니다. 이렇게 하면 기본 클래스에서 가상 함수를 효과적으로 숨깁니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

다음 샘플에서는 C4263를 생성 합니다.

```cpp
// C4263.cpp
// compile with: /W4
#pragma warning(default:4263)
#pragma warning(default:4264)
class B {
public:
   virtual void func();
};

class D : public B {
   void func(int);   // C4263
};

int main() {
}
```
