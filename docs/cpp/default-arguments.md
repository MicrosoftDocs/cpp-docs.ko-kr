---
title: 기본 인수 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arguments [C++], function
- function declarators
- functions [C++], default arguments
- declaring functions [C++], declarators
- default arguments
- arguments [C++], default
- defaults [C++], arguments
ms.assetid: d32cf516-05cb-4d4d-b169-92f5649fdfa2
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 88c341abab34595da58d435be28f50e86cb47403
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="default-arguments"></a>기본 인수
많은 경우에 함수에는 기본값이면 충분할 정도로 가끔 사용되는 인수가 있습니다. 이러한 경우 기본 인수 기능을 사용하면 지정된 호출에서 의미가 있는 인수만 함수에 지정할 수 있습니다. 이 개념을 설명 하는 것이 좋습니다에 제시 된 예에서는 [함수 오버 로드](../cpp/function-overloading.md)합니다.  
  
```  
// Prototype three print functions.  
int print( char *s );                  // Print a string.  
int print( double dvalue );            // Print a double.  
int print( double dvalue, int prec );  // Print a double with a  
//  given precision.  
```  
  
 많은 응용 프로그램에서 `prec`에 대한 적절한 기본값을 제공하여 두 함수의 필요성을 없앨 수 있습니다.  
  
```  
// Prototype two print functions.  
int print( char *s );                    // Print a string.  
int print( double dvalue, int prec=2 );  // Print a double with a  
//  given precision.  
```  
  
 구현에서 `print` 함수 형식에 대 한 이러한 함수가 하나만 있는지 사실을 반영 하므로 약간 변경 되어 **double**:  
  
```  
// default_arguments.cpp  
// compile with: /EHsc /c  
  
// Print a double in specified precision.  
//  Positive numbers for precision indicate how many digits  
//  precision after the decimal point to show. Negative  
//  numbers for precision indicate where to round the number  
//  to the left of the decimal point.  
  
#include <iostream>  
#include <math.h>  
using namespace std;  
  
int print( double dvalue, int prec ) {  
   // Use table-lookup for rounding/truncation.  
   static const double rgPow10[] = {   
      10E-7, 10E-6, 10E-5, 10E-4, 10E-3, 10E-2, 10E-1, 10E0,  
         10E1,  10E2,  10E3,  10E4, 10E5,  10E6  
   };  
   const int iPowZero = 6;  
   // If precision out of range, just print the number.  
   if( prec >= -6 && prec <= 7 )  
      // Scale, truncate, then rescale.  
      dvalue = floor( dvalue / rgPow10[iPowZero - prec] ) *  
      rgPow10[iPowZero - prec];  
   cout << dvalue << endl;  
   return cout.good();  
}  
```  
  
 새 `print` 함수를 호출하려면 다음과 같은 코드를 사용합니다.  
  
```  
print( d );    // Precision of 2 supplied by default argument.  
print( d, 0 ); // Override default argument to achieve other  
//  results.  
```  
  
 기본 인수를 사용하는 경우 다음 사항에 유의하세요.  
  
-   기본 인수는 후행 인수가 생략되는 함수 호출에서만 사용되며 마지막 인수여야 합니다. 따라서 다음 코드는 올바르지 않습니다.  
  
    ```  
    int print( double dvalue = 0.0, int prec );  
    ```  
  
-   기본 인수는 다시 지정한 정의가 원래 정의와 동일한 경우에도 이후 선언에서 다시 정의할 수 없습니다. 따라서 다음 코드는 오류를 생성합니다.  
  
    ```  
    // Prototype for print function.  
    int print( double dvalue, int prec = 2 );  
  
    ...  
  
    // Definition for print function.  
    int print( double dvalue, int prec = 2 )  
    {  
    ...  
    }  
    ```  
  
     이 코드의 문제는 정의에 있는 함수 선언이 `prec`의 기본 인수를 다시 정의하는 것입니다.  
  
-   이후 선언에서 기본 인수를 더 추가할 수 있습니다.  
  
-   함수에 대한 포인터에 기본 인수를 제공할 수 있습니다. 예:  
  
    ```  
    int (*pShowIntVal)( int i = 0 );  
    ```  
  
## <a name="see-also"></a>참고 항목  
 