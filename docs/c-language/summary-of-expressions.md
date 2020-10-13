---
title: 식 요약
ms.date: 06/14/2018
ms.assetid: ed448953-687a-4b57-a1cb-12967bd770ea
ms.openlocfilehash: 1660690c6d36aa1dbdc025d6afe92e19ff941463
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220836"
---
# <a name="summary-of-expressions"></a>식 요약

*primary-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*string-literal*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(**  *expression*  **)**

*expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression*  **,**  *assignment-expression*

*constant-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*

*conditional-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*  **?**  *expression*  **:**  *conditional-expression*

*assignment-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*conditional-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-expression* *assignment-operator* *assignment-expression*

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*primary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **[**  *expression*  **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **(**  *argument-expression-list*<sub>opt</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **.**  *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **->**  *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **--**

*argument-expression-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-list*  **,**  *assignment-expression*

*unary-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **++**  *unary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **--**  *unary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-operator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cast-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **`sizeof`**  *unary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sizeof (**  *type-name*  **)**

*unary-operator*: 다음 중 하나<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **&** **&#42;** **+** **-** **~** **!**

*cast-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(**  *type-name*  **)**  *cast-expression*

*multiplicative-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cast-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*  **&#42;**  *cast-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*  **/**  *cast-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*  **%**  *cast-expression*

*additive-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression*  **+**  *multiplicative-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression*  **-**  *multiplicative-expression*

*shift-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression*  **\<\<**  *additive-expression*<br/> &nbsp;&nbsp;&nbsp;&nbsp;* shift-expression*  **>>**  *additive-expression*

*relational-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*  **\<**  *shift-expression*<br/> &nbsp;&nbsp;&nbsp;&nbsp;* relational-expression*  **>**  *shift-expression*<br/> &nbsp;&nbsp;&nbsp;&nbsp;* relational-expression*  **\<=**  *shift-expression*<br/> &nbsp;&nbsp;&nbsp;&nbsp;* relational-expression*  **>=**  *shift-expression*

*equality-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*equality-expression*  **==**  *relational-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*equality-expression*  **!=**  *relational-expression*

*AND-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*equality-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*AND-expression*  **&**  *equality-expression*

*exclusive-OR-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*AND-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*exclusive-OR-expression*  **^**  *AND-expression*

*inclusive-OR-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*exclusive-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inclusive-OR-expression*  **&#124;**  *exclusive-OR-expression*

*logical-AND-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inclusive-OR-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-AND-expression*  **&&**  *inclusive-OR-expression*

*logical-OR-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-AND-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*logical-OR-expression*  **&#124;&#124;**  *logical-AND-expression*

## <a name="see-also"></a>참조

- [구 구조 문법](../c-language/phrase-structure-grammar.md)
