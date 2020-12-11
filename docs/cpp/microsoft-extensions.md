---
description: '자세한 정보: Microsoft 확장'
title: Microsoft 확장명
ms.date: 11/04/2016
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
ms.openlocfilehash: f3a6bfb7e85c3b219d1dda67e051f731ecf54fe6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161640"
---
# <a name="microsoft-extensions"></a>Microsoft 확장명

*`asm-statement`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__asm`***`assembly-instruction`* **`;`** <sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__asm {`***`assembly-instruction-list`* **`} ;`** <sub>opt</sub>  

*`assembly-instruction-list`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`assembly-instruction`* **`;`** <sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`assembly-instruction`***`;`** *`assembly-instruction-list`* **`;`** <sub>opt</sub>

*`ms-modifier-list`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *`ms-modifier`* *`ms-modifier-list`* <sub>opt</sub>

*`ms-modifier`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__cdecl`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__fastcall`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__stdcall`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__syscall`** (이후 구현을 위해 예약 됨)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__oldcall`** (이후 구현을 위해 예약 됨)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__unaligned`** (이후 구현을 위해 예약 됨)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`based-modifier`*

*`based-modifier`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__based (`** *`based-type`* **`)`**

*`based-type`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`name`*
