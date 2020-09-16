---
title: 컴파일러 오류 C3904
ms.date: 11/04/2016
f1_keywords:
- C3904
helpviewer_keywords:
- C3904
ms.assetid: 08297605-e4f2-4c6c-b637-011f1fd40631
ms.openlocfilehash: b2c5737a4442761cbaa84b532907e579eddb423d
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686067"
---
# <a name="compiler-error-c3904"></a>컴파일러 오류 C3904

' property_accessor ': 숫자 매개 변수를 지정 해야 합니다.

`get`속성 차원에 대해 및 메서드의 매개 변수 수를 확인 합니다 `set` .

- 메서드에 대 한 매개 변수의 수는 `get` 속성 차원의 수와 동일 하거나 인덱싱되지 않은 속성의 경우 0 이어야 합니다.

- 메서드의 매개 변수 개수는 `set` 속성의 차원 수보다 하나 이상 커야 합니다.

자세한 내용은 [property](../../extensions/property-cpp-component-extensions.md)을 참조하세요.

## <a name="examples"></a>예제

다음 샘플에서는 C3904를 생성 합니다.

```cpp
// C3904.cpp
// compile with: /clr /c
ref class X {
   property int P {
      // set
      void set();   // C3904
      // try the following line instead
      // void set(int);

      // get
      int get(int, int);   // C3904
      // try the following line instead
      // int get();
   };
};
```

다음 샘플에서는 C3904를 생성 합니다.

```cpp
// C3904b.cpp
// compile with: /clr /c
ref struct X {
   property int Q[double, double, float, float, void*, int] {
      // set
      void set(double, void*);   // C3904
      // try the following line instead
      // void set(double, double, float, float, void*, int, int);

      // get
      int get();   // C3904
      // try the following line instead
      // int get(double, double, float, float, void*, int);
   }
};
```
