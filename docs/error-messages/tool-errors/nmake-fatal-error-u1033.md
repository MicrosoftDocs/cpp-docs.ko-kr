---
title: NMAKE 심각한 오류 U1033 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1033
dev_langs:
- C++
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1d39d4c35ec66d405d51d601b7c5d2b2ab37b02
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319272"
---
# <a name="nmake-fatal-error-u1033"></a>NMAKE 심각한 오류 U1033
구문 오류: 예기치 않은 ' string'  
  
 문자열이 유효한 구문은 메이크파일의 일부가 아닙니다.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>다음과 같은 가능한 원인을 확인하여 수정하려면  
  
1.  닫는 꺾쇠 괄호의 짝이 없으면 (**<<**) 인라인 파일은 한 줄의 시작 부분에 다음 오류가 발생 합니다.  
  
    ```  
    syntax error : 'EOF' unexpected  
    ```  
  
2.  등호 기호 메이크파일의 매크로 정의 포함 된 경우 (**=**) 앞에 오는 이름을 지정 하거나 이름을 정의 되는 경우이 nothing으로 확장 되는 매크로, 다음과 같은 오류가 발생 합니다.  
  
    ```  
    syntax error : '=' unexpected  
    ```  
  
3.  경우 세미콜론 (**;**) 도구에서 주석 줄에 있습니다. INI 않습니다는 줄의 시작 부분에 다음 오류가 발생 합니다.  
  
    ```  
    syntax error : ';' unexpected  
    ```  
  
4.  메이크파일의 워드 프로세서에서 서식을 다음과 같은 오류가 발생할 수 있습니다.  
  
    ```  
    syntax error : ':' unexpected  
    ```