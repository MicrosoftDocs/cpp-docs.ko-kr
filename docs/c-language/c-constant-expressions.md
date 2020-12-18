---
description: '자세한 정보: C 상수 식'
title: C 상수 식
ms.date: 06/14/2018
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: d48a6c47-e44c-4be2-9c8b-7944c7ef8de7
ms.openlocfilehash: 82da5150b35035d96b28ff1091e754cb7043a5ca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289519"
---
# <a name="c-constant-expressions"></a>C 상수 식

상수 식은 런타임이 아닌 컴파일 타임에 계산되며, 상수를 사용할 수 있는 모든 위치에서 사용될 수 있습니다. 상수 식은 해당 형식에 대한 표현 가능한 값의 범위에 있는 상수로 계산되어야 합니다. 상수 식의 피연산자는 정수 상수, 문자 상수, 부동 소수점 상수, 열거형 상수, 형식 캐스트, **`sizeof`** 식 및 기타 상수 식일 수 있습니다.

## <a name="syntax"></a>구문

*constant-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*

*conditional-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression* **?** *expression* **:** *conditional-expression*

*expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression* **,** *assignment-expression*

*assignment-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-expression* *assignment-operator* *assignment-expression*

*assignment-operator*: 다음 중 하나<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **=** **&#42;=** **/=** **%=** **+=** **-=** **\<\<=** **>>=** **&=** **^=** **&#124;=**

구조체 선언자, 열거자, 직접 선언자, 직접 추상 선언자 및 레이블 문의 비단말에는 *onstant-expression* 비단말이 포함됩니다.

정수 상수 식은 구조체의 비트 필드 멤버 크기, 열거형 상수의 값, 배열의 크기 또는 **`case`** 상수의 값을 지정하는 데 사용해야 합니다.

전처리기 지시문에서 사용된 상수 식에는 제한이 추가로 적용됩니다. 따라서 이러한 상수 식을 "제한된 상수 식"이라고 합니다. 제한된 상수 식은 **`sizeof`** 식, 열거형 상수, 모든 형식에 대한 형식 캐스트 또는 부동 형식 상수를 포함할 수 없습니다. 그러나 특수 상수 식인 **defined (** _identifier_ **)** 를 포함할 수 있습니다.

## <a name="see-also"></a>참조

- [피연산자 및 식](../c-language/operands-and-expressions.md)
