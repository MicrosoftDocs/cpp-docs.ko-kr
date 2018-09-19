---
title: 컴파일러 오류 C3904 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3904
dev_langs:
- C++
helpviewer_keywords:
- C3904
ms.assetid: 08297605-e4f2-4c6c-b637-011f1fd40631
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4453d39b93000116b3547ff5047e6837c8d34e6a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46135985"
---
# <a name="compiler-error-c3904"></a>컴파일러 오류 C3904

'property_accessor': 숫자 매개 변수를 지정 해야 합니다

매개 변수 개수를 확인 하 `get` 고 `set` 속성 차원에 대해 메서드.

- 에 대 한 매개 변수 개수는 `get` 메서드 속성의 차원 수와 동일 해야 합니다 또는 인덱싱되지 않은 속성에 대 한 0 이어야 합니다.

- 매개 변수 개수는 `set` 메서드는 하나 여야 합니다 차원 속성의 수를 초과 합니다.

자세한 내용은 [property](../../windows/property-cpp-component-extensions.md)을 참조하세요.

## <a name="example"></a>예제

다음 샘플 C3904를 생성합니다.

```
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

## <a name="example"></a>예제

다음 샘플 C3904를 생성합니다.

```
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