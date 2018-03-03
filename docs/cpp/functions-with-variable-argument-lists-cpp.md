---
title: "가변 인수 목록 (c + +)를 사용 하 여 함수 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arguments [C++], variable number of
- variable argument lists
- declarators, functions
- argument lists [C++], variable number of
- declaring functions [C++], variables
- function calls, variable number of arguments
ms.assetid: 27c2f83a-21dd-44c6-913c-2834cb944703
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a715662ac6680218e3b15822108f429733569bfa
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/25/2018
---
# <a name="functions-with-variable-argument-lists--c"></a>가변 인수를 사용 하는 함수 목록 (c + +)
마지막 멤버가 줄임표(...)인 함수 선언에서는 여러 가지 인수를 사용할 수 있습니다. 이러한 경우 C++에서는 명시적으로 선언된 인수에만 형식 검사를 제공합니다. 인수의 수와 형식까지 변경될 수 있는 정도의 일반적인 수준으로 함수를 만들어야 하는 경우 가변 인수 목록을 사용할 수 있습니다. 함수는 집합은 가변 인수 목록을 사용 하는 함수의 예입니다. `printf` *인수 선언 목록*  
  
## <a name="functions-with-variable-arguments"></a>가변 인수를 사용하는 함수  
 표준 포함 파일에 포함 된 매크로 사용 하 여 선언 된 후 인수에 액세스 하려면 \<g. h > 아래에서 설명 합니다.  
  
 **Microsoft 전용**  
  
 Microsoft C++에서는 줄임표가 마지막 인수이고 줄임표 앞에 쉼표가 있는 경우 줄임표를 인수로 지정할 수 있습니다. 따라서 `int Func( int i, ... );` 선언은 올바르지만 `int Func( int i ... );`는 올바르지 않습니다.  
  
 **Microsoft 전용 종료**  
  
 일정하지 않은 수의 인수를 사용하는 함수의 선언에는 사용하지 않더라도 최소한 하나의 자리 표시자 인수가 있어야 합니다. 이 자리 표시자 인수가 제공되지 않은 경우 나머지 인수에 액세스할 수 있는 방법은 없습니다.  
  
 `char` 형식의 인수는 가변 인수로 전달될 때 `int` 형식으로 변환됩니다. 마찬가지로, 형식 인수 **float** 전달 되는 가변 인수로 형식으로 변환 됩니다 **double**합니다. 다른 형식의 인수에는 일반적인 정수 계열 및 부동 소수점 확장이 적용됩니다. 참조 [표준 변환](standard-conversions.md) 자세한 정보에 대 한 합니다.  
  
 변수 목록이 필요한 함수는 인수 목록에서 줄임표(...)를 사용하여 선언합니다. 형식 및에 설명 된 매크로 사용 하 여는 \<g. h > 변수 목록에서 전달 되는 인수를 액세스 하는 파일을 포함 합니다. 이러한 매크로 대 한 자세한 내용은 참조 [va_arg, va_copy, va_end, va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)합니다. 참조하세요.  
  
 다음 예제에서는 매크로 형식과 함께 작동 하는 방법을 보여 줍니다 (에 선언 된 \<g. h >): 
  
```  
// variable_argument_lists.cpp  
#include <stdio.h>  
#include <stdarg.h>  
  
//  Declaration, but not definition, of ShowVar.  
void ShowVar( char *szTypes, ... );  
int main() {  
   ShowVar( "fcsi", 32.4f, 'a', "Test string", 4 );  
}  
  
//  ShowVar takes a format string of the form  
//   "ifcs", where each character specifies the  
//   type of the argument in that position.  
//  
//  i = int  
//  f = float  
//  c = char  
//  s = string (char *)  
//  
//  Following the format specification is a variable   
//  list of arguments. Each argument corresponds to   
//  a format character in the format string to which   
// the szTypes parameter points   
void ShowVar( char *szTypes, ... ) {  
   va_list vl;  
   int i;  
  
   //  szTypes is the last argument specified; you must access   
   //  all others using the variable-argument macros.  
   va_start( vl, szTypes );  
  
   // Step through the list.  
   for( i = 0; szTypes[i] != '\0'; ++i ) {  
      union Printable_t {  
         int     i;  
         float   f;  
         char    c;  
         char   *s;  
      } Printable;  
  
      switch( szTypes[i] ) {   // Type to expect.  
         case 'i':  
            Printable.i = va_arg( vl, int );  
            printf_s( "%i\n", Printable.i );  
         break;  
  
         case 'f':  
             Printable.f = va_arg( vl, double );  
             printf_s( "%f\n", Printable.f );  
         break;  
  
         case 'c':  
             Printable.c = va_arg( vl, char );  
             printf_s( "%c\n", Printable.c );  
         break;  
  
         case 's':  
             Printable.s = va_arg( vl, char * );  
             printf_s( "%s\n", Printable.s );  
         break;  
  
         default:  
         break;  
      }  
   }  
   va_end( vl );  
}  
//Output:   
// 32.400002  
// a  
// Test string  
```  
  
 앞의 예제는 다음과 같은 중요한 개념을 설명합니다.  
  
1.  가변 인수에 액세스하기 전에 `va_list` 형식의 변수로 목록 표시를 설정해야 합니다. 앞의 예제에서 표식 이름은 `vl`입니다.  
  
2.  `va_arg` 매크로를 사용하여 각각의 인수에 액세스합니다. 스택에서 올바른 바이트 수가 전송할 수 있도록 `va_arg` 매크로에 검색 인수의 형식을 설명해야 합니다. 호출 프로그램에서 제공한 것과 다른 잘못된 크기 형식을 `va_arg`로 지정하는 경우 결과를 예측할 수 없습니다.  
  
3.  `va_arg` 매크로를 원하는 형식에 사용하여 얻은 결과를 명시적으로 캐스팅해야 합니다.  
  
 가변 인수 처리를 종료하려면 매크로를 호출해야 합니다.`va_end`