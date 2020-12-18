---
description: '자세한 정보: 복합 문 (C)'
title: 복합 문 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- compound statements
- statements, compound
ms.assetid: 32d1bf86-cbbc-42a9-ba3a-1be1c6c7754c
ms.openlocfilehash: b4c1ee15bc081c34cbc12bfe2c3e997ca181b7be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293445"
---
# <a name="compound-statement-c"></a>복합 문 (C)

"블록"이라고도 하는 복합 문은 일반적으로 **`if`** 문 같은 다른 문의 본문으로 나타납니다. [선언 및 형식](../c-language/declarations-and-types.md)에서는 복합 문 헤드에 나타날 수 있는 선언의 형태와 의미에 대해 설명합니다.

## <a name="syntax"></a>구문

*compound-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *declaration-list*<sub>opt</sub> *statement-list*<sub>opt</sub> **}**

*declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-list* *declaration*

*statement-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement-list* *statement*

선언이 있을 경우 모든 문 앞에 와야 합니다. 복합 문의 시작 지점에 선언된 각 식별자의 범위는 블록의 끝 지점까지 확장됩니다. 내부 블록에 동일한 식별자의 선언이 없는 경우 블록 전체에 표시됩니다.

**`extern`** 만 가능한 함수를 제외하고 **`register`** , **`static`** 또는 **`extern`** 을 사용하여 명시적으로 선언되지 않은 복합 문의 식별자는 **`auto`** 로 간주됩니다. 함수 선언에서 **`extern`** 지정자를 해제할 수 있으며 함수는 여전히 **`extern`** 입니다.

복합 문에서 변수 또는 함수를 선언할 때 스토리지 클래스 **`extern`** 을 사용하지 않으면 스토리지가 할당되지 않고 초기화가 허용되지 않습니다. 선언은 외부 변수나 다른 곳에서 정의된 함수를 참조합니다.

**`auto`** 또는 **`register`** 키워드를 사용하여 블록에서 선언된 변수는 다시 할당되고, 필요한 경우 복합 문이 시작될 때마다 초기화됩니다. 이 변수는 복합 문이 종료된 후에는 정의되지 않습니다. 블록 내부에서 선언된 변수에 **`static`** 특성이 있는 경우 프로그램 실행이 시작되고 프로그램 전체에 해당 값을 유지하면 변수가 초기화됩니다. **`static`** 에 대한 자세한 내용은 [스토리지 클래스](../c-language/c-storage-classes.md)를 참조하세요.

다음 예제는 복합 문에 대해 설명합니다.

```C
if ( i > 0 )
{
    line[i] = x;
    x++;
    i--;
}
```

이 예제에서 `i`가 0보다 클 경우 복합 문 내부의 모든 문이 순서대로 실행됩니다.

## <a name="see-also"></a>참조

[문](../c-language/statements-c.md)
