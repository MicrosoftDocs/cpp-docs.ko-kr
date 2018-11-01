---
title: 컴파일러 오류 C3646
ms.date: 06/14/2018
f1_keywords:
- C3646
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
ms.openlocfilehash: df2e52631ed75cc4a473429ea35e136ed0a88f98
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50606728"
---
# <a name="compiler-error-c3646"></a>컴파일러 오류 C3646

> 'specifier': 알 수 없는 재정의 지정자

## <a name="remarks"></a>설명

컴파일러는 재정의 지정자를 찾을 것으로 예상 했지만 토큰 컴파일러에서 인식할 수 없습니다 위치에는 토큰을 찾았습니다.

예를 들어 경우를 인식할 수 없는 *지정자* 됩니다 **_NOEXCEPT**, 키워드로 대체 **noexcept**합니다.

자세한 내용은 [재정의 지정자](../../windows/override-specifiers-cpp-component-extensions.md)합니다.

## <a name="example"></a>예제

다음 샘플 C3646 생성 및이 해결 하는 방법을 보여 줍니다.

```cpp
// C3646.cpp
// compile with: /clr /c
ref class C {
   void f() unknown;   // C3646
   // try the following line instead
   // virtual void f() abstract;
};
```