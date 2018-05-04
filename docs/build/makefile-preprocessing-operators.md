---
title: 메이크파일 연산자 전처리 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], makefile preprocessing
- EXIST operator
- preprocessing NMAKE makefile operators
- NMAKE program, operators
- DEFINED operator
- makefiles, preprocessing operators
ms.assetid: a46e4d39-afdb-43c1-ac3b-025d33e6ebdb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9a99bf6388a4aa15b2126aca8e09210b7202d46
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="makefile-preprocessing-operators"></a>메이크파일 전처리 연산자
메이크파일 전처리 식에서는 상수 값, 명령의 종료 코드, 문자열, 매크로 및 파일 시스템 경로에 대해 작동하는 연산자를 사용할 수 있습니다. 식을 평가하기 위해 전처리기에서는 먼저 매크로를 확장하고 명령을 실행한 다음 연산을 수행합니다. 연산은 괄호로 명시적으로 그룹화된 순서에 따르고 그 다음에는 연산자의 우선 순위에 따라 평가됩니다. 결과는 상수 값입니다.  
  
 `DEFINED` 연산자는 매크로 이름에 작동하는 논리 연산자입니다. 식 `DEFINED(` *매크로 이름* `)` 참인 경우 *매크로 이름* 할당된 된 값에 없는 경우에 정의 됩니다. `DEFINED` 또는 `!IF`와 함께 `!ELSE IF`는 `!IFDEF` 또는 `!ELSE IFDEF`와 동일합니다. 그러나 이러한 지시문과 달리 `DEFINED`는 복합 식에서 사용할 수 있습니다.  
  
 `EXIST` 연산자는 파일 시스템 경로에 작동하는 논리 연산자입니다. `EXIST(`*경로* `)` 참인 경우 *경로* 존재 합니다. `EXIST`의 결과는 이진 식에서 사용할 수 있습니다. 경우 *경로* 에 공백이 있는 경우 큰따옴표로 묶어야 합니다.  
  
 문자열 두 개를 비교하려면 같음(`==`) 연산자 또는 같지 않음(`!=`) 연산자를 사용합니다. 문자열은 큰따옴표로 묶습니다.  
  
 정수 상수는 숫자 부정(`-`), 숫자 부정의 보수(`~`) 및 논리 부정(`!`)에 단항 연산자를 사용할 수 있습니다.  
  
 식에서는 다음 연산자를 사용할 수 있습니다. 우선 순위가 동일한 연산자는 함께 그룹화되고 그룹은 우선 순위에 따라 내림차순으로 나열됩니다. 단항 연산자는 오른쪽 피연산자에 연결됩니다. 동일한 우선 순위의 이항 연산자는 왼쪽에서 오른쪽으로 피연산자를 연결합니다.  
  
|연산자|설명|  
|--------------|-----------------|  
|`DEFINED(` *매크로 이름* `)`|현재 정의 상태에 대 한 논리 값을 생성 *매크로 이름*합니다.|  
|`EXIST(` *경로* `)`|파일의 존재에 대 한 논리 값을 생성 *경로*합니다.|  
|||  
|`!`|단항 논리 연산자 NOT|  
|`~`|단항 연산자의 보수|  
|`-`|단항 부정 연산자|  
|||  
|`*`|곱하기|  
|`/`|나누기|  
|`%`|모듈러스(나머지)|  
|||  
|`+`|더하기|  
|`-`|빼기|  
|||  
|`<<`|비트 왼쪽으로 시프트|  
|`>>`|비트 오른쪽으로 시프트|  
|||  
|`<=`|보다 작거나 같음|  
|`>=`|보다 크거나 같음|  
|`<`|보다 작음|  
|`>`|보다 큼|  
|||  
|`==`|같음|  
|`!=`|같지 않음|  
|||  
|`&`|비트 AND|  
|`^`|비트 XOR|  
|`&#124;`|비트 OR|  
|||  
|`&&`|논리적 AND|  
|||  
|`&#124;&#124;`|논리적 OR|  
  
> [!NOTE]
>  비트 XOR 연산자(`^`)는 이스케이프 문자와 동일하므로 식에서 사용되는 경우 이스케이프되어야 합니다(예: `^^`).  
  
## <a name="see-also"></a>참고 항목  
 [메이크파일 전처리 식](../build/expressions-in-makefile-preprocessing.md)