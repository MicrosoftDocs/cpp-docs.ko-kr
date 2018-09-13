---
title: 문자열 리터럴 요약 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: d2693900-f4e2-4820-b7de-085d51827aee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a94d575ee36f38b56f64fb6298eb6f6f6e43567e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762745"
---
# <a name="summary-of-string-literals"></a>문자열 리터럴 요약

*string-literal*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**'** *s-char-sequence*<sub>opt</sub> **'**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L'** *s-char-sequence*sub>opt</sub> **'**  
  
*s-char-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char-sequence* *s-char*  
  
*s-char*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;큰따옴표("), 백슬래시(\\) 또는 줄 바꿈 문자를 제외한 소스 문자 집합의 멤버  

## <a name="see-also"></a>참고 항목

[어휘 문법](../c-language/lexical-grammar.md)