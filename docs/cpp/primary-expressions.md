---
title: 기본 식 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- primary expressions
- expressions [C++], name
- expressions [C++], literal
- expressions [C++], primary
- expressions [C++], qualified names
ms.assetid: 8ef9a814-6058-4b93-9b6e-e8eb8350b1ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3c419bf65a02d13359335bc6cb527fc189d596d6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="primary-expressions"></a>기본 식
기본 식은 더 복잡한 식의 구성 요소이며 리터럴, 이름 및 범위 결정 연산자(`::`)로 정규화된 이름입니다.  기본 식의 형식은 다음 중 하나입니다.  
  
```  
  
      literal  
      this  
:: namename( expression )  
```  
  
 A *리터럴* 상수 기본 식입니다. 지정의 형태에 따라 형식이 결정됩니다. 참조 [리터럴](../cpp/numeric-boolean-and-pointer-literals-cpp.md) 리터럴 지정 하는 방법에 대 한 자세한 내용은 합니다.  
  
 **이** 키워드는 클래스 개체에 대 한 포인터입니다. 비정적 멤버 함수 안에 사용할 수 있으며 함수가 호출된 인스턴스에 대한 클래스의 인스턴스를 가리킵니다. **이** 키워드 클래스 멤버 함수의 본문 밖에 사용할 수 없습니다.  
  
 유형의 **이** 포인터가 `type`  **\*const** (여기서 `type` 클래스 이름) 수정 되지 않은 함수는 **이** 포인터입니다. 함수 선언 및 종류의 다음 예제에서는 멤버 **이**:  
  
```  
// expre_Primary_Expressions.cpp  
// compile with: /LD  
class Example  
{  
public:  
    void Func();          //  * const this  
    void Func() const;    //  const * const this  
    void Func() volatile; //  volatile * const this  
};  
```  
  
 참조 [이 포인터](this-pointer.md) 형식을 수정 하는 방법에 대 한 자세한 내용은 **이** 포인터입니다.  
  
 이름 앞의 범위 결정 연산자(`::`)는 기본 식을 구성합니다.  이러한 이름은 멤버 이름이 아니라 전역 범위의 이름이어야 합니다.  이름의 선언이 이 식의 형식을 결정합니다. 선언 이름이 l-value인 경우 l-value이므로 대입 연산자 식의 왼쪽에 나타날 수 있습니다. 범위 결정 연산자를 사용하면 전역 이름이 현재 범위에서 숨겨지더라도 해당 이름이 참조됩니다. 참조 [범위](../cpp/scope-visual-cpp.md) 범위 결정 연산자를 사용 하는 방법의 예입니다.  
  
 괄호로 묶은 식은 그 형식과 값이 괄호로 묶지 않은 식과 동일한 기본 식입니다. 괄호로 묶지 않은 식이 l-value일 경우 l-value입니다.  
  
 위는 기본 식 구문의 컨텍스트에서 *이름* 의미에 대 한 설명 된 구문을에 아무 것도 [이름](http://msdn.microsoft.com/en-us/1c49cc24-08d5-4884-b170-ba8ed42d80db)경우, 형식의 이름은 이름 앞의 범위 결정 연산자를 사용 하 여 클래스에만 발생할 수 있습니다 사용할 수 없습니다.  사용자 정의 변환 함수 이름과 소멸자 이름이 여기에 포함됩니다.  
  
 기본 식의 예제는 다음과 같습니다.  
  
```  
100 // literal  
'c' // literal  
this // in a member function, a pointer to the class instance  
::func // a global function  
::operator + // a global operator function  
::A::B // a global qualified name  
( i + 1 ) // a parenthesized expression  
```  
  
 다음 예제에서는 모든 고려할 *이름*, 및 다양 한 형태로 따라서 기본 식:  
  
```  
MyClass // a identifier  
MyClass::f // a qualified name  
operator = // an operator function name  
operator char* // a conversion operator function name  
~MyClass // a destructor name  
A::B   // a qualified name  
A<int> // a template id  
```  
  
## <a name="see-also"></a>참고 항목  
 [식의 형식](../cpp/types-of-expressions.md)