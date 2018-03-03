---
title: "문자 형식 | Microsoft Docs"
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
- character data types [C]
- types [C], character
ms.assetid: d3ca8cda-c0d7-43af-9472-697e8ef015ce
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a48382f5f7a3ab64518c44ec953005cd54a4fe03
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="character-types"></a>문자 형식
**L** 문자가 앞에 오지 않는 정수 문자 상수는 `int` 형식입니다. 단일 문자가 포함된 정수 문자 상수의 값은 정수로 해석된 문자의 숫자 값입니다. 예를 들어 `a` 문자의 숫자 값은 10진수로 97이고 16진수로 61입니다.  
  
 구문적으로 "와이드 문자 상수"는 **L** 문자가 앞에 붙는 문자 상수입니다. 와이드 문자 상수의 형식은 STDDEF.H 헤더 파일에 정의된 정수 형식인 `wchar_t`입니다. 예:  
  
```  
char    schar =  'x';   /* A character constant          */  
wchar_t wchar = L'x';   /* A wide-character constant for   
                            the same character           */  
```  
  
 와이드 문자 상수는 너비가 16비트이며 확장된 실행 문자 집합의 멤버를 지정합니다. 와이드 문자 상수를 사용하면 `char` 형식으로 표현하기에는 너무 큰 알파벳 문자를 표현할 수 있습니다. 와이드 문자에 대한 자세한 내용은 [멀티바이트 및 와이드 문자](../c-language/multibyte-and-wide-characters.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [C 문자 상수](../c-language/c-character-constants.md)