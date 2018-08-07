---
title: C 형식 지정자 | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type specifiers, C
- specifiers, type
ms.assetid: fbe13441-04c3-4829-b047-06d374adc2b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e37ac421627d4c4503d75eaf65188bbe234af015
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32388385"
---
# <a name="c-type-specifiers"></a>C 형식 지정자

선언에 있는 형식 지정자는 변수 또는 함수 선언의 형식을 정의합니다.

## <a name="syntax"></a>구문

*type-specifier*:  
&nbsp;&nbsp;**void**  
&nbsp;&nbsp;**char**  
&nbsp;&nbsp;**short**  
&nbsp;&nbsp;**int**  
&nbsp;&nbsp;**long**  
&nbsp;&nbsp;**float**  
&nbsp;&nbsp;**double**  
&nbsp;&nbsp;**signed**  
&nbsp;&nbsp;**unsigned**  
&nbsp;&nbsp;*struct-or-union-specifier*  
&nbsp;&nbsp;*enum-specifier*  
&nbsp;&nbsp;*typedef-name*  

**signed char**, **signed int**, **signed short int** 및 **signed long int** 형식은 상응하는 **unsigned** 및 **enum**과 함께 *정수* 형식이라고 불립니다. **float**, **double** 및 **long double** 형식 지정자는 *부동* 또는 *부동 소수점* 형식이라고 합니다. 변수 또는 함수 선언에서 정수 계열 또는 부동 소수점 형식 지정자를 사용할 수 있습니다. *type-specifier*가 선언에서 제공되지 않으면 **int**로 간주됩니다.

선택적 키워드 **signed** 및 **unsigned**는 **enum**을 제외한 정수 계열 형식의 앞이나 뒤에 올 수 있으며, 형식 지정자로 단독으로 사용될 수도 있는데 이 경우 각각 **signed int** 및 **unsigned int**로 해석됩니다. 단독으로 사용될 때 **int** 키워드는 **signed**로 간주되고, **long** 및 **short**는 **long int** 및 **short int**로 해석됩니다.

열거형 형식은 기본 형식으로 간주됩니다. 열거형 형식에 대한 형식 지정자는 [열거형 선언](../c-language/c-enumeration-declarations.md)에서 설명합니다.

**void** 키워드는 세 가지 용도가 있습니다. 함수 반환 형식을 지정하고, 인수를 사용하지 않는 함수의 인수 형식 목록을 지정하며, 지정되지 않은 형식에 대한 포인터를 지정합니다. **void** 형식을 사용하여 값을 반환하지 않는 함수를 선언하거나 지정되지 않은 형식에 대한 포인터를 선언할 수 있습니다. 함수 이름 뒤의 괄호 안에 단독으로 나타나는 **void**에 대한 자세한 내용은 [인수](../c-language/arguments.md)를 참조하세요.

**Microsoft 전용**

형식 검사는 이제 ANSI 규격이며, 이는 **short** 및 **int** 형식이 고유한 형식임을 의미합니다. 예를 들어 다음은 Microsoft C 컴파일러의 이전 버전에서 허용하던 재정의입니다.

```C
int   myfunc();
short myfunc();
```

다음 예제에서는 다른 형식에 대한 간접 참조를 나타내는 경고도 생성합니다.

```C
int *pi;
short *ps;

ps = pi;  /* Now generates warning */
```

Microsoft C 컴파일러에서는 부호의 차이에 대한 경고도 생성합니다. 예:

```C
signed int *pi;
unsigned int *pu

pi = pu;  /* Now generates warning */
```

**void** 형식의 식은 파생 작업에 대해 평가됩니다. 어떤 방식으로든 **void** 형식인 식의 존재하지 않는 값을 사용할 수 없으며, **void** 식을 암시적 또는 명시적 변환을 통해 **void**를 제외한 형식으로 변환할 수 없습니다. **void** 식이 필요한 컨텍스트에서 다른 형식의 식을 사용하는 경우 해당 값은 무시됩니다.

ANSI 사양을 따르려면 **void\*\*** 를 **int\*\*** 로 사용할 수 없습니다. **void\*** 만 지정되지 않은 형식에 대한 포인터로 사용할 수 있습니다.

**Microsoft 전용 종료**

[Typedef 선언](../c-language/typedef-declarations.md)에 설명된 대로 **typedef** 선언으로 추가 형식 지정자를 만들 수 있습니다. 각 형식의 크기에 대한 자세한 내용은 [기본 형식의 저장소](../c-language/storage-of-basic-types.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

[선언 및 형식](../c-language/declarations-and-types.md)  
