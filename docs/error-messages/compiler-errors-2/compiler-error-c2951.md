---
description: '자세한 정보: 컴파일러 오류 C2951'
title: 컴파일러 오류 C2951
ms.date: 11/04/2016
f1_keywords:
- C2951
helpviewer_keywords:
- C2951
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
ms.openlocfilehash: 7f3030764cdd36d40fbd78a8c3768c7dc1085c21
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322109"
---
# <a name="compiler-error-c2951"></a>컴파일러 오류 C2951

형식 선언은 전역, 네임 스페이스 또는 클래스 범위 에서만 허용 됩니다.

전역 또는 네임 스페이스 범위 외부에서 제네릭 또는 템플릿 클래스를 선언할 수 없습니다. 제네릭 또는 템플릿 선언을 포함 파일에서 수행 하는 경우 포함 파일이 전역 범위에 있는지 확인 합니다.

다음 샘플에서는 C2951를 생성 합니다.

```cpp
// C2951.cpp
template <class T>
class A {};

int main() {
   template <class T>   // C2951
   class B {};
}
```

제네릭을 사용 하는 경우에도 C2951이 발생할 수 있습니다.

```cpp
// C2951b.cpp
// compile with: /clr /c

// OK
generic <class T>
ref class GC { };

int main() {
   generic <class T> ref class GC2 {};   // C2951
}
```
