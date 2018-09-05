---
title: ALIAS (MASM) | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Alias
dev_langs:
- C++
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6a977d35040d8ca25cd3bd4ae4def233092b37a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691064"
---
# <a name="alias-masm"></a>ALIAS (MASM)

합니다 **별칭** 지시문을 함수에 대 한 대체 이름을 만듭니다.  이 함수에 대해 여러 이름을 만들거나 링커 (LINK.exe)를 새 함수로 이전 함수에 매핑할 수 있는 라이브러리를 만들 수 있습니다.

## <a name="syntax"></a>구문

> 별칭 \< *별칭*> = \< *실제 이름*>

#### <a name="parameters"></a>매개 변수

*실제 이름*<br/>
함수 또는 프로시저의 실제 이름입니다.  꺾쇠 괄호는 필수입니다.

*alias*<br/>
대체 또는 별칭 이름입니다.  꺾쇠 괄호는 필수입니다.

## <a name="see-also"></a>참고자료

[지시문 참조](../../assembler/masm/directives-reference.md)<br/>