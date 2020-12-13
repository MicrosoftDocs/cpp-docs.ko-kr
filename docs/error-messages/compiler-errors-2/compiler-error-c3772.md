---
description: '자세한 정보: 컴파일러 오류 C3772'
title: 컴파일러 오류 C3772
ms.date: 11/04/2016
f1_keywords:
- C3772
helpviewer_keywords:
- C3772
ms.assetid: 63e938d4-088d-41cc-a562-5881a05b5710
ms.openlocfilehash: 679c5bc47e9b31ebf085dec63a46549a10484cac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340127"
---
# <a name="compiler-error-c3772"></a>컴파일러 오류 C3772

'name': friend 템플릿 선언이 잘못되었습니다.

클래스 템플릿 특수화의 friend를 선언하는 것은 유효하지 않습니다. 클래스 템플릿의 명시적 또는 부분 특수화를 선언하고 동일한 문에서 해당 특수화의 friend를 선언할 수는 없습니다. *name* 자리 표시자는 잘못된 선언을 식별합니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

- 클래스 템플릿 특수화의 friend를 선언하지 마세요.

- 애플리케이션에 해당하는 경우 클래스 템플릿의 friend를 선언하거나 특정 부분 또는 명시적 특수화의 friend를 선언합니다.

## <a name="example"></a>예제

다음 코드 예제는 클래스 템플릿 부분 특수화의 friend를 선언하므로 실패합니다.

```cpp
// c3772.cpp
// compile with: /c

// A class template.
    template<class T> class A {};

// A partial specialization of the class template.
    template<class T> class A<T*> {};

// An explicit specialization.
    template<> class A<char>;

class X {
// Invalid declaration of a friend of a partial specialization.
    template<class T> friend class A<T*>; // C3772

// Instead, if it is appropriate for your application, declare a
// friend of the class template. Consequently, all specializations
// of the class template are friends:
//    template<class T> friend class A;
// Or declare a friend of a particular partial specialization:
//    friend class A<int*>;
// Or declare a friend of a particular explicit specialization:
//    friend class A<char>;
};
```

## <a name="see-also"></a>참고 항목

[템플릿](../../cpp/templates-cpp.md)<br/>
[템플릿 특수화](../../cpp/template-specialization-cpp.md)
