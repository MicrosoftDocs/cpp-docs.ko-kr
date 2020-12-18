---
description: '자세한 정보: 가변적인 개수의 인수를 사용하여 호출'
title: 가변적인 개수의 인수를 사용하여 호출
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- arguments [C++], variable number of
- VARARGS.H
- ellipsis (...), variable number of arguments
- STDARGS.H
- function calls, arguments
- '... ellipsis'
- function calls, variable number of arguments
ms.assetid: 8808fb26-4822-42f5-aba3-ac64b54e151b
ms.openlocfilehash: 4e30759d25d7dd3b5b3bcb69c0edc0e97849c7e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214144"
---
# <a name="calls-with-a-variable-number-of-arguments"></a>가변적인 개수의 인수를 사용하여 호출

쉼표 뒤에 마침표 3개( **, ...** )가 오는 줄임표 표기법으로 부분적 매개 변수 목록을 종료하여 함수에 전달되는 인수가 더 있을 수도 있지만 관련 정보가 더 이상 없음을 나타낼 수 있습니다. 이 인수에 대해 형식 검사를 수행하지 않습니다. 줄임표 표기법 앞에 하나 이상의 매개 변수가 와야 하며 매개 변수 목록에서 줄임표 표기법이 마지막 토큰이어야 합니다. 줄임표 표기법을 사용하지 않으면 매개 변수 목록에 선언된 매개 변수 외에 매개 변수가 수신될 경우 함수의 동작이 정의되지 않습니다.

인수의 개수가 일정하지 않은 함수를 호출하려면 함수 호출에 인수를 몇 개 지정하십시오. 예를 들어, C 런타임 라이브러리의 `printf` 함수가 있습니다. 함수 호출은 매개 변수 목록이나 인수 형식 목록에 선언된 형식 이름마다 인수를 하나씩 포함해야 합니다.

**`__fastcall`** 호출 규칙이 지정되지 않으면 함수 호출에 지정된 모든 인수가 스택에 배치됩니다. 함수에 대해 선언된 매개 변수 개수에 따라 스택에서 가져와 매개 변수에 할당할 인수의 개수가 결정됩니다. 스택에서 추가 인수를 검색하고 사용할 인수의 개수를 결정해야 합니다. STDARG.H 파일에는 일정하지 않은 개수의 인수를 사용하는 암수의 인수에 액세스하기 위한 ANSI 스타일 매크로가 있습니다. VARARGS.H에 있는 XENIX 스타일 매크로도 계속 지원됩니다.

다음은 일정하지 않은 개수의 인수를 호출하는 함수에 대한 샘플 선언입니다.

```
int average( int first, ...);
```

## <a name="see-also"></a>참조

[함수 호출](../c-language/function-calls.md)
