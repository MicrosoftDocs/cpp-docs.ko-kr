---
title: 범위 및 표시 영역 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- scope, levels
- visibility
- file scope [C++]
ms.assetid: a019eb7c-66ed-46a7-bc9f-89a963930a56
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b85f0ca180fc60b1281440845289d2f2a39d71af
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32389191"
---
# <a name="scope-and-visibility"></a>범위 및 표시 영역
식별자의 "표시 유형"은 "범위"를 참조할 수 있는 프로그램의 위치를 결정합니다. 식별자는 "범위"로 포함된 프로그램 부분에서만 표시되며(예: 사용 가능) 나타나는 파일, 함수, 블록 또는 함수 프로토타입으로 제한될 수 있습니다(제한이 증가하는 순서). 식별자의 범위는 이름을 사용할 수 있는 프로그램의 일부입니다. 이를 "어휘 범위"라고도 합니다. 범위에는 함수, 파일, 블록 및 함수 프로토타입과 같은 네 가지 종류가 있습니다.  
  
 레이블을 제외한 모든 식별자에는 선언이 발생하는 수준에서 결정된 범위가 있습니다. 각 범위 종류에 대한 다음 규칙은 프로그램 내의 식별자의 표시 유형을 관리합니다.  
  
 파일 범위  
 파일 범위의 식별자에 대한 선언자 또는 형식 지정자는 블록 밖이나 매개 변수의 목록에 나타나고 선언 뒤의 변환 단위에 있는 어느 위치에서도 액세스할 수 있습니다. 파일 범위의 식별자 이름은 종종 "전역" 또는 "외부"라고 합니다. 전역 식별자의 범위는 정의 또는 선언 시점부터 시작하여 변환 단위의 끝에서 종료됩니다.  
  
 함수 범위  
 레이블은 함수 범위가 있는 유일한 종류의 식별자입니다. 레이블은 문에서 사용하여 암시적으로 선언됩니다. 레이블 이름은 함수 내에서 고유해야 합니다. 레이블 및 레이블 이름에 대한 자세한 내용은 [goto 및 Labeled 문](../c-language/goto-and-labeled-statements-c.md)을 참조하세요.  
  
 블록 범위  
 블록 범위를 포함하는 식별자에 대한 선언자 또는 형식 지정자는 블록 안이나 함수 정의에 있는 정식 매개 변수 선언의 목록에 나타납니다. 선언 또는 정의 지점부터 해당 선언 또는 정의가 포함된 블록의 끝까지만 표시됩니다. 범위는 해당 블록 및 해당 블록에 중첩된 모든 블록으로 제한되며 연결된 블록을 닫는 중괄호에서 끝납니다. 이러한 식별자는 대개 "지역 변수" 라고 합니다.  
  
 함수 프로토타입 범위  
 함수 프로토타입 범위를 포함하는 식별자에 대한 선언자 또는 형식 지정자는 함수 프로토타입(함수 선언의 일부가 아님)의 매개 변수 선언 목록 내에 나타납니다. 해당 범위는 함수 선언자 끝에서 종료됩니다.  
  
 다른 소스 파일에서 변수를 화면에 표시하기에 적절한 선언은 [저장소 클래스](../c-language/c-storage-classes.md)에서 설명합니다. 하지만 **static** 저장소 클래스 지정자를 사용하여 외부 수준에서 선언한 변수와 함수는 정의된 소스 파일 내에서만 표시됩니다. 다른 모든 함수는 전역적으로 표시됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [수명, 범위, 표시 유형 및 링크](../c-language/lifetime-scope-visibility-and-linkage.md)