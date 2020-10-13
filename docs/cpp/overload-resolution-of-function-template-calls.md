---
title: 함수 템플릿 호출의 오버로드 확인
ms.date: 11/04/2016
helpviewer_keywords:
- function templates overload resolution
ms.assetid: a2918748-2cbb-4fc6-a176-e256f120bee4
ms.openlocfilehash: 7b7e374328b6d234426d8263e4c6655191133700
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008906"
---
# <a name="overload-resolution-of-function-template-calls"></a>함수 템플릿 호출의 오버로드 확인

함수 템플릿은 동일한 이름의 비템플릿 함수를 오버로드할 수 있습니다. 이 시나리오에서 함수 호출은 첫 번째 템플릿 인수 추론을 사용하여 고유한 특수화를 통해 함수 템플릿을 인스턴스화할 수 있습니다. 템플릿 인수 추론이 실패하는 경우 다른 함수 오버로드가 호출을 해결하기 위해 고려됩니다. 후보 집합이라고도 불리는 이러한 다른 오버로드는 비템플릿 함수와 다른 인스턴스화된 함수 템플릿을 포함합니다. 템플릿 인수 추론이 성공하는 경우 생성된 함수는 오버로드 확인 규칙에 따라 다른 함수와 비교하여 최상의 경우를 결정합니다. 자세한 내용은 [함수 오버 로드](function-overloading.md)를 참조 하세요.

## <a name="example-choose-a-nontemplate-function"></a>예: 비템플릿 함수 선택

비템플릿 함수가 템플릿 함수와 동일하게 일치하는 경우 다음 예제에서 템플릿 인수가 명시적으로 지정되지 않은 경우 비템플릿 함수가 호출 `f(1, 1)`로써 선택됩니다.

```cpp
// template_name_resolution9.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

void f(int, int) { cout << "f(int, int)" << endl; }
void f(char, char) { cout << "f(char, char)" << endl; }

template <class T1, class T2>
void f(T1, T2)
{
   cout << "void f(T1, T2)" << endl;
};

int main()
{
   f(1, 1);   // Equally good match; choose the nontemplate function.
   f('a', 1); // Chooses the template function.
   f<int, int>(2, 2);  // Template arguments explicitly specified.
}
```

```Output
f(int, int)
void f(T1, T2)
void f(T1, T2)
```

## <a name="example-exact-match-template-function-preferred"></a>예: 정확한 일치 템플릿 함수 기본 설정

다음 예제는 비템플릿 함수를 변환해야 하는 경우 정확하게 일치하는 템플릿 함수가 선호됨을 보여 줍니다.

```cpp
// template_name_resolution10.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

void f(int, int) { cout << "f(int, int)" << endl; }

template <class T1, class T2>
void f(T1, T2)
{
   cout << "void f(T1, T2)" << endl;
};

int main()
{
   long l = 0;
   int i = 0;
   // Call the template function f(long, int) because f(int, int)
   // would require a conversion from long to int.
   f(l, i);
}
```

```Output
void f(T1, T2)
```

## <a name="see-also"></a>참조

[이름 확인](../cpp/templates-and-name-resolution.md)<br/>
[t](../cpp/typename.md)
