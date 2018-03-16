---
title: "C 곱하기 연산자 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- arithmetic operators [C++], multiplicative operators
- / operator
- / operator, multiplicative operators
- remainder operator (%)
- operators [C], multiplication
- '% operator'
- slash (/) operator
- multiplication operator [C++], multiplicative operators
ms.assetid: 495471c9-319b-4eb4-bd97-039a025fd3a9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c8fbcbb5579c63ef0cab375ec19e2afee47e97ee
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2018
---
# <a name="c-multiplicative-operators"></a>곱하기 연산자
곱하기 연산자는 곱하기(**\***), 나누기(**/**) 및 나머지(`%`) 연산을 수행합니다.  
  
 **구문**  
  
 *multiplicative-expression*:  
 *cast-expression*  
  
 *multiplicative-expression*  **\***  *cast-expression*  
  
 *multiplicative-expression*  **/**  *cast-expression*  
  
 *multiplicative-expression*  **%**  *cast-expression*  
  
 나머지 연산자의 피연산자(`%`)는 정수 계열이어야 합니다. 곱하기(**\***) 및 나누기(**/**) 연산자는 정수 계열 또는 부동 형식 피연산자를 사용할 수 있습니다. 따라서 피연산자의 형식은 다를 수도 있습니다.  
  
 곱셈 연산자는 피연산자에 대한 일반적인 산술 변환을 수행합니다. 결과 형식은 변환 후의 피연산자 형식과 동일합니다.  
  
> [!NOTE]
>  곱셈 연산자로 수행된 변환은 오버플로 또는 언더플로 조건을 제공하지 않으므로 변환 후 곱셈 연산 결과가 피연산자 형식으로 표현되지 않는 경우 정보가 손실될 수 있습니다.  
  
 아래에서 C 곱셈 연산자를 설명합니다.  
  
|연산자|설명|  
|--------------|-----------------|  
|**\***|곱셈 연산자를 사용하면 두 개의 피연산자가 곱해집니다.|  
|**/**|나누기 연산자를 사용하면 첫 번째 피연산자가 두 번째 피연산자로 나눠집니다. 두 정수 피연산자를 나눈 결과가 정수가 아닌 경우 다음과 같은 규칙에 따라 잘립니다.|  
||-   0으로 나누기 결과는 ANSI C 표준에 따라 정의되지 않습니다. Microsoft C 컴파일러는 컴파일 타임이나 런타임에서 오류를 발생시킵니다.|  
||-   두 피연산자 모두 양수 또는 부호 없는 피연산자인 경우 결과는 0으로 잘립니다.|  
||-   피연산자 중 하나가 음수인 경우 연산 결과가 대수 몫보다 작거나 같은 최대 정수인지 또는 대수 몫보다 크거나 같은 최소 정수인지가 정의되는 구현입니다. (아래의 Microsoft 전용 섹션을 참조하십시오.)|  
|`%`|나머지 연산자 결과는 첫 번째 피연산자를 두 번째 피연산자로 나눈 나머지입니다. 나누기가 정확하지 않은 경우 결과는 다음 규칙에 따라 결정됩니다.|  
||-   오른쪽 피연산자가 0이면 결과가 정의되지 않습니다.|  
||-   두 피연산자 모두 양수 또는 부호 없는 피연산자인 경우 결과는 양수입니다.|  
||-   한 피연산자가 음수이고 결과가 정확하지 않은 경우 결과는 정의된 구현입니다. (아래의 Microsoft 전용 섹션을 참조하십시오.)|  
  
 **Microsoft 전용**  
  
 한 피연산자가 음수인 나누기에서는 0으로 잘립니다.  
  
 나머지 연산자를 사용한 나누기에서 한 연산이 음수인 경우 결과는 피제수(식의 첫 번째 피연산자)와 기호가 동일합니다.  
  
 **Microsoft 전용 종료**  
  
## <a name="examples"></a>예제  
 아래의 선언은 다음 예제에서 사용합니다.  
  
```  
int i = 10, j = 3, n;  
double x = 2.0, y;  
```  
  
 이 문은 곱셈 연산자를 사용합니다.  
  
```  
y = x * i;  
```  
  
 이 경우 `x`를 `i`로 곱하여 20.0이라는 값을 제공합니다. 결과는 **double** 형식입니다.  
  
```  
n = i / j;  
```  
  
 이 예제에서는 10을 3으로 나눕니다. 결과는 0으로 잘려 정수 값 3을 생성합니다.  
  
```  
n = i % j;  
```  
  
 이 문은 10을 3으로 나눌 때 `n`에 정수 나머지 1을 할당합니다.  
  
 **Microsoft 전용**  
  
 나머지의 부호는 피제수의 부호와 동일합니다. 예를 들어:  
  
```  
50 % -6 = 2  
-50 % 6 = -2  
```  
  
 각각의 경우에 `50` 및 `2`의 부호는 동일합니다.  
  
 **Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [곱하기 연산자 및 나머지 연산자](../cpp/multiplicative-operators-and-the-modulus-operator.md)