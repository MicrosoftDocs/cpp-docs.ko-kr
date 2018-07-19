---
title: 전처리기 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3bb5a9740bab3f69ff66a51cd58e6e1378e178f0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33848452"
---
# <a name="preprocessor"></a>전처리기
전처리기는 첫 번째 변환 단계의 일부로 소스 파일의 텍스트를 조작하는 텍스트 처리기입니다. 전처리기는 소스 텍스트를 구문 분석하지 않지만 매크로 호출을 찾기 위해 소스 텍스트를 토큰으로 나눕니다. 컴파일러는 일반적으로 첫 번째 단계에서 전처리기를 호출하지만, 컴파일 없이 텍스트를 처리하기 위해 전처리기를 별도로 호출할 수도 있습니다.  
  
 전처리기에 대한 참조 자료에는 다음 단원이 포함되어 있습니다.  
  
-   [전처리기 지시문](../preprocessor/preprocessor-directives.md)  
  
-   [전처리기 연산자](../preprocessor/preprocessor-operators.md)  
  
-   [미리 정의 된 매크로](../preprocessor/predefined-macros.md)  
  
-   [pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)  
  
 **Microsoft 전용**  
  
 사용 하 여 전처리 후 소스 코드의 목록을 가져올 수 있습니다는 [/E](../build/reference/e-preprocess-to-stdout.md) 또는 [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) 컴파일러 옵션입니다. 두 옵션 모두 전처리기를 호출하고 결과 텍스트를 표준 출력 장치(대부분의 경우 콘솔)에 출력합니다. 두 옵션의 차이점은 /E는 `#line` 지시문을 포함하고 /EP는 이러한 지시문을 제거한다는 점입니다.  
  
 **Microsoft 전용 종료**  
  
##  <a name="_predir_special_terminology"></a> 특수 용어  
 전처리기 설명서에서 "인수"라는 용어는 함수에 전달되는 엔터티를 나타냅니다. 경우에 따라 함수 호출에서 지정된 인수 식과 함수 정의에서 지정된 인수 선언을 각각 나타내는 "실제" 또는 "형식"이라는 수식어가 인수에 붙습니다.  
  
 "변수"라는 용어는 간단한 C 형식 데이터 개체를 나타냅니다. "개체"라는 용어는 C++ 개체 및 변수를 둘 다 나타내는 포괄적인 용어입니다.  
  
## <a name="see-also"></a>참고 항목  
 [C/c + + 전처리기 참조](../preprocessor/c-cpp-preprocessor-reference.md)   
 [변환 단계](../preprocessor/phases-of-translation.md)