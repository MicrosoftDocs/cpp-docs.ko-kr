---
title: _SCL_SECURE_NO_WARNINGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
dev_langs:
- C++
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 285e54a2eab4d116df81c3e10c597c6dbb6dd9cb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS
C++ 표준 라이브러리에서 안전하지 않을 수 있는 메서드 중 하나를 호출하면 [컴파일러 경고(수준 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)이 표시됩니다. 이 경고를 비활성화하려면 코드에서 매크로 **_SCL_SECURE_NO_WARNINGS**를 정의합니다.  
  
```  
#define _SCL_SECURE_NO_WARNINGS  
```  
  
## <a name="remarks"></a>설명  
 C4996 경고를 비활성화하는 다른 방법은 다음과 같습니다.  
  
-   [/D(전처리기 정의)](../build/reference/d-preprocessor-definitions.md) 컴파일러 옵션을 사용합니다.  
  
 ```  
    cl /D_SCL_SECURE_NO_WARNINGS [other compiler options] myfile.cpp  
```  
  
-   [/w](../build/reference/compiler-option-warning-level.md) 컴파일러 옵션을 사용합니다.  
  
 ```  
    cl /wd4996 [other compiler options] myfile.cpp  
```  
  
-   [#pragma warning](../preprocessor/warning.md) 경고를 사용합니다.  
  
 ```  
 #pragma warning(disable:4996)  
```  
  
 또한 c 4996와 함께 경고 수준의 수동으로 변경할 수는 **/w\<l >\< n>**  컴파일러 옵션입니다. 예를 들어 C4996 경고를 수준 4로 설정하려면 다음 코드를 사용합니다.  
  
```  
cl /w44996 [other compiler options] myfile.cpp  
```  
  
 자세한 내용은 [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX(경고 수준)](../build/reference/compiler-option-warning-level.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [안전한 라이브러리: C++ 표준 라이브러리](../standard-library/safe-libraries-cpp-standard-library.md)

