---
description: '자세한 정보: for 문(C)'
title: for 문 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- for keyword [C]
ms.assetid: 560a8de4-19db-4868-9f18-dbe51b17900d
ms.openlocfilehash: 4e20529ccec4f586f8785e122903b22be42e69a2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97196024"
---
# <a name="for-statement-c"></a>for 문 (C)

**`for`** 문을 사용하면 지정한 횟수만큼 문 또는 복합 문을 반복할 수 있습니다. **`for`** 문의 본문은 선택적 조건이 false가 될 때까지 0번 이상 실행됩니다. **`for`** 문 내에 선택적 식을 사용하여 **`for`** 문의 실행 중 값을 초기화하고 변경할 수 있습니다.

## <a name="syntax"></a>구문

*iteration-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`for`** **(** *init-expression*<sub>opt</sub> **;** *cond-expression*<sub>opt</sub> **;** *loop-expression*<sub>opt</sub> **)** *statement*

**`for`** 문의 실행 절차는 다음과 같습니다.

1. *init-expression* 이 계산됩니다(있는 경우). 이로 인해 루프에 대한 초기화가 지정됩니다. *init-expression* 의 형식에 대한 제한은 없습니다.

1. *cond-expression* 이 계산됩니다(있는 경우). 이 식에는 산술 또는 포인터 형식이 있어야 합니다. 이 식은 각 반복 전에 계산됩니다. 세 가지 결과가 나타날 수 있습니다.

   - *cond-expression* 이 **`true`** (0이 아님)이고 *statement* 가 실행되면 *loop-expression* 이 계산됩니다(있는 경우). *loop-expression* 은 각 반복 후 계산됩니다. 해당 형식에 대한 제한은 없습니다. 의도하지 않은 결과가 순서대로 실행됩니다. 그런 다음 *cond-expression* 이 계산되며 프로세스가 다시 시작됩니다.

   - *cond-expression* 을 생략할 경우 *cond-expression* 이 true로 간주되고 이전 단락의 설명에 따라 실행이 진행됩니다. *cond-expression* 인수가 없는 **`for`** 문은 문 본문 내의 **`break`** 또는 **`return`** 문이 실행되거나 **`for`** 문 본문 외부에 있는 레이블 문으로의 **`goto`** 가 실행될 때만 종료됩니다.

   - *cond-expression* 이 **`false`** (0)일 경우 **`for`** 문의 실행이 종료되고 프로그램의 다음 문으로 제어가 전달됩니다.

**`for`** 문은 문 본문 내의 **`break`** , **`goto`** 또는 **`return`** 문이 실행될 때도 종료됩니다. **`for`** 루프의 **`continue`** 문을 실행하면 *loop-expression* 이 계산됩니다. **`for`** 루프 내에서 **`break`** 문이 실행되면 *loop-expression* 이 계산 또는 실행되지 않습니다. 다음 문은

```C
for( ; ; )
```

**`break`** , **`goto`** 또는 **`return`** 문을 사용해야만 종료할 수 있는 무한 루프를 생성하는 일반적인 방법입니다.

## <a name="example"></a>예제

이 예제에서는 **`for`** 문에 대해 설명합니다.

```C
// c_for.c
int main()
{
   char* line = "H e  \tl\tlo World\0";
   int space = 0;
   int tab = 0;
   int i;
   int max = strlen(line);
   for (i = 0; i < max; i++ )
   {
      if ( line[i] == ' ' )
      {
          space++;
      }
      if ( line[i] == '\t' )
      {
          tab++;
      }
   }

   printf("Number of spaces: %i\n", space);
   printf("Number of tabs: %i\n", tab);
   return 0;
}
```

## <a name="output"></a>출력

```Output
Number of spaces: 4
Number of tabs: 2
```

## <a name="see-also"></a>참조

[문](../c-language/statements-c.md)
