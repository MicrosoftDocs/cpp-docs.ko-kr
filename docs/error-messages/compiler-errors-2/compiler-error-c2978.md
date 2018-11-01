---
title: 컴파일러 오류 C2978
ms.date: 11/04/2016
f1_keywords:
- C2978
helpviewer_keywords:
- C2978
ms.assetid: 5e7bee82-e266-4ccd-ad2e-ee89606ec5bf
ms.openlocfilehash: 25798e793bec7d09ea1f307ec1e2d9a63b9dbe27
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428108"
---
# <a name="compiler-error-c2978"></a>컴파일러 오류 C2978

구문 오류: 'keyword1' 또는 'keyword2'가 필요한데 'keyword3' 형식이 있습니다. 제네릭에서는 비형식 매개 변수를 사용할 수 없습니다.

제네릭 클래스가 잘못 선언되었습니다. 참조 [제네릭](../../windows/generics-cpp-component-extensions.md)자세한 내용은 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C2978을 생성합니다.

```
// C2978.cpp
// compile with: /clr /c
generic <ref class T>   // C2978
// try the following line instead
// generic <typename T>   // OK
ref class Utils {
   static void sort(T elems, size_t size);
};

generic <int>
// try the following line instead
// generic <class T>
ref class Utils2 {
   static void sort(T elems, size_t size);
};
```