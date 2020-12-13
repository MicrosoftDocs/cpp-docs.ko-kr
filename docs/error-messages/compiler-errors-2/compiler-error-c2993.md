---
description: '자세한 정보: 컴파일러 오류 C2993'
title: 컴파일러 오류 C2993
ms.date: 11/04/2016
f1_keywords:
- C2993
helpviewer_keywords:
- C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
ms.openlocfilehash: 2c43d4f3e54378d419f1945b1f6b38e9ee4d9758
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136424"
---
# <a name="compiler-error-c2993"></a>컴파일러 오류 C2993

' identifier ': 형식이 아닌 템플릿 매개 변수 ' parameter '의 형식이 잘못 되었습니다.

구조체 또는 공용 구조체 인수를 사용 하 여 템플릿을 선언할 수 없습니다. 포인터를 사용 하 여 구조체 및 공용 구조체를 템플릿 매개 변수로 전달 합니다.

다음 샘플에서는 C2993를 생성 합니다.

```cpp
// C2993.cpp
// compile with: /c
// C2993 expected
struct MyStruct {
   int a;char b;
};

template <class T, struct MyStruct S>   // C2993

// try the following line instead
// template <class T, struct MyStruct * S>
class CMyClass {};
```

이 오류는 Visual Studio .NET 2003에서 수행한 컴파일러 규칙 작업의 결과로도 생성 됩니다. 부동 소수점 비 형식 템플릿 매개 변수는 더 이상 허용 되지 않습니다. C + + 표준은 부동 소수점 비 형식 템플릿 매개 변수를 허용 하지 않습니다.

함수 템플릿인 경우 함수 인수를 사용 하 여 부동 소수점 비 형식 템플릿 매개 변수를 전달 합니다 .이 코드는 Visual Studio .NET 2003 및 Visual Studio .NET 버전의 Visual C++에서 유효 합니다. 클래스 템플릿인 경우에는 쉽게 해결할 수 없습니다.

```cpp
// C2993b.cpp
// compile with: /c
template<class T, float f> void func(T) {}   // C2993

// OK
template<class T>   void func2(T, float) {}
```
