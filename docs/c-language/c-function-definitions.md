---
description: '자세한 정보: C 함수 정의'
title: C 함수 정의
ms.date: 11/04/2016
helpviewer_keywords:
- function declarators
- function definitions
- declaring functions, about function declarations
- declaring functions, declarators
- functions [C], parameters
- declarators, functions
- function parameters, function definitions
- function body
- declaring functions, variables
ms.assetid: ebab23c8-6eb8-46f3-b21d-570cd8457a80
ms.openlocfilehash: 9e664224608a741897bf8ae6208a0d9011cdb3c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296929"
---
# <a name="c-function-definitions"></a>C 함수 정의

함수 정의는 함수의 이름, 받아야 하는 매개 변수의 형식과 개수 및 반환 형식을 지정합니다. 함수 정의는 지역 변수의 선언과 함수의 기능을 결정하는 문이 있는 함수 본문도 포함합니다.

## <a name="syntax"></a>구문

*translation-unit*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*external-declaration* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*translation-unit* *external-declaration*

*external-declaration*: /\* 외부(파일) 범위에만 허용됨 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*function-definition*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*

*function-definition*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\* *attribute-seq* 는 Microsoft 전용임 \*/

프로토타입 매개 변수인 경우:

*declaration-specifiers*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-list* *declaration*

*declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator*: /\* 함수 선언자 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *parameter-type-list*  **)**  /\* 새로운 스타일의 선언자 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **(** *identifier-list*<sub>opt</sub> **)**  /\* 사용되지 않는 스타일의 선언자 \*/

정의의 매개 변수 목록에서는 다음 구문을 사용합니다.

*parameter-type-list*: /\* 매개 변수 목록 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **, ...**

*parameter-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **,**  *parameter-declaration*

*parameter-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *abstract-declarator*<sub>opt</sub>

이전 스타일의 함수 정의에 있는 매개 변수 목록에서는 다음 구문을 사용합니다.

*identifier-list*: /\* 사용되지 않는 스타일의 함수 정의 및 선언에 사용됨 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier-list* **,**  *identifier*

함수 본문에 대한 구문은 다음과 같습니다.

*compound-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *declaration-list*<sub>opt</sub> *statement-list*<sub>opt</sub> **}**

함수 선언을 수정할 수 있는 유일한 스토리지 클래스 지정자는 **`extern`** 및 **`static`** 입니다. **`extern`** 지정자는 다른 파일에서 함수를 참조할 수 있음을 나타냅니다. 즉, 함수 이름이 링커로 내보내집니다. **`static`** 지정자는 다른 파일에서 함수를 참조할 수 없음을 나타냅니다. 즉, 이름이 링커에 의해 내보내지지 않습니다. 스토리지 클래스가 함수 정의에 없을 경우 **`extern`** 으로 간주됩니다. 어떤 경우이든 함수는 정의 지점에서 파일의 끝까지 항상 표시됩니다.

선택적 *declaration-specifiers* 및 필수 *declarator* 는 함께 함수의 반환 형식 및 이름을 지정합니다. *declarator* 는 함수를 명명하는 식별자와 함수 이름 뒤에 나오는 괄호의 조합입니다. 선택적 *attribute-seq* 비터미널은 [함수 특성](../c-language/function-attributes.md)에 정의된 Microsoft 고유의 기능입니다.

*declarator* 구문의 *direct-declarator* 는 정의될 함수의 이름과 매개 변수의 식별자를 지정합니다. *direct-declarator* 에 *parameter-type-list* 가 포함된 경우 목록은 모든 매개 변수의 형식을 지정합니다. 이러한 선언자는 이후의 함수 호출을 위해 함수 프로토타입의 역할도 합니다.

함수 정의의 *declaration-list* 에 있는 *declaration* 에는 **`register`** 가 아닌 *storage-class-specifier* 가 포함될 수 없습니다. **`register`** 스토리지 클래스가 **`int`** 형식의 값에 지정된 경우에만 *declaration-specifiers* 구문에서 *type-specifier* 를 생략할 수 있습니다.

*compound-statement* 는 지역 변수 선언, 외부에서 선언된 항목에 대한 참조 및 문이 포함된 함수 본문입니다.

[함수 특성](../c-language/function-attributes.md), [스토리지 클래스](../c-language/storage-class.md), [반환 형식](../c-language/return-type.md), [매개 변수](../c-language/parameters.md) 및 [함수 본문](../c-language/function-body.md) 섹션에서는 함수 정의의 구성 요소에 대해 자세히 설명합니다.

## <a name="see-also"></a>참조

[함수](../c-language/functions-c.md)
