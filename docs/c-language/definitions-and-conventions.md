---
title: 정의 및 규칙 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- nonterminals definition
ms.assetid: f9b3cf5f-6a7c-4a10-9b18-9d4a43efdaeb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99f227f37f4a9de92f244df5988f7ee8088e41d5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="definitions-and-conventions"></a>정의 및 규칙
구문 정의에서 단말은 끝점입니다. 다른 확인은 가능하지 않습니다. 단말에는 예약어와 사용자 정의 식별자의 집합이 포함됩니다.  
  
 비단말은 구문의 자리 표시자이며 이 구문 요약의 다른 곳에서 정의됩니다. 정의는 재귀적일 수 있습니다.  
  
 선택적 구성 요소는 첨자 opt로 나타냅니다. 예를 들어 개체에 적용된  
  
```  
  
{  
expression <SUB>opt</SUB> }  
```  
  
 중괄호로 묶인 선택적 식을 나타냅니다.  
  
 구문 규칙은 구문의 구성 요소마다 다른 글꼴 특성을 사용합니다. 기호 및 글꼴은 다음과 같습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|*nonterminal*|기울임꼴은 비터미널을 나타냅니다.|  
|**const**|굵게 표시된 터미널은 다음과 같이 입력해야 할 리터럴 예약어 및 기호입니다. 이 컨텍스트의 문자는 항상 대/소문자를 구분합니다.|  
|opt|뒤에 opt가 오는 비터미널은 항상 선택 사항입니다.|  
|default typeface|이 서체로 설명되거나 나열된 집합의 문자는 C 문에서 단말로 사용할 수 있습니다.|  
  
 비터미널 뒤에 오는 콜론(**:**)은 정의를 지정합니다. 대체 정의는 "one of"라는 단어가 앞에 오는 경우를 제외하고 별도의 줄에 나열됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [C 언어 구문 요약](../c-language/c-language-syntax-summary.md)