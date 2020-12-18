---
description: '자세한 정보: 단순 변수 선언'
title: 단순 변수 선언
ms.date: 11/04/2016
helpviewer_keywords:
- untyped variables
- declaring variables, simple
ms.assetid: b07adf9d-9e79-4b64-8a34-e6fe1c7eccec
ms.openlocfilehash: ccb63ad3726d8a5ed5692abd5ec678a1b517614d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114626"
---
# <a name="simple-variable-declarations"></a>단순 변수 선언

직접 선언자의 가장 간단한 형태로 단순 변수를 선언하여 변수의 이름 및 형식을 지정합니다. 이 선언에서 변수의 스토리지 클래스와 데이터 형식도 지정합니다.

변수 선언에는 스토리지 클래스나 형식 또는 둘 다 필요합니다. 형식화되지 않은 변수(예: `var;`)는 경고를 생성합니다.

## <a name="syntax"></a>구문

*declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*

*identifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *digit*

산술, 구조체, 공용 구조체, 열거형 및 void 형식과 **`typedef`** 이름으로 나타내는 형식의 경우 형식 지정자가 모든 형식 정보를 제공하므로 선언에 단순 선언자를 사용할 수 있습니다. 포인터, 배열 및 함수 형식에는 복잡한 선언자가 필요합니다.

쉼표( **,** )로 구분된 식별자 목록을 사용하여 같은 선언에 여러 변수를 지정할 수 있습니다. 선언에 정의된 모든 변수의 기본 형식은 같습니다. 예를 들어:

```C
int x, y;        /* Declares two simple variables of type int */
int const z = 1; /* Declares a constant value of type int */
```

`x` 및 `y` 변수는 특정 구현에 대해 **`int`** 형식으로 정의된 집합에 값을 보유할 수 있습니다. 단순 개체 `z`가 값 1로 초기화되며 수정할 수 없습니다.

`z`의 선언이 초기화되지 않은 정적 변수용이거나 파일 범위에 있을 경우 초기 값 0을 수신하고 이 값은 수정할 수 없습니다.

```C
unsigned long reply, flag; /* Declares two variables
                              named reply and flag     */
```

이 예제에서 `reply` 변수와 `flag` 변수 모두 **`unsigned long`** 형식이고 부호 없는 정수 계열 값을 갖습니다.

## <a name="see-also"></a>참조

[선언자 및 변수 선언](../c-language/declarators-and-variable-declarations.md)
