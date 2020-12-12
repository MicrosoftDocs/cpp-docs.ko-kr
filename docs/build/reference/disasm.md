---
description: 자세히 알아보기:/DISASM
title: /DISASM
ms.date: 01/17/2018
f1_keywords:
- /disasm
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
ms.openlocfilehash: 764754e017958a57afd53236b7fc1ffb6217d850
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192904"
---
# <a name="disasm"></a>/DISASM

DUMPBIN 출력의 코드 섹션 디스어셈블리를 인쇄 합니다.

## <a name="syntax"></a>Syntax

> **/DISASM**{**:** \[ **BYTES** | **NOBYTES**]}

### <a name="arguments"></a>인수

**바이트**<br/>
디스어셈블리 출력에 해석 된 opcode 및 인수와 함께 명령 바이트를 포함 합니다. 기본 옵션입니다.

**NOBYTES**<br/>
디스어셈블리 출력에는 명령 바이트를 포함 하지 않습니다.

## <a name="remarks"></a>설명

**/DISASM** 옵션은 파일의 코드 섹션 디스어셈블리를 표시 합니다. 파일에 있는 경우 디버그 기호를 사용 합니다.

**/DISASM** 는 관리 되지 않는 네이티브 이미지 에서만 사용 해야 합니다. 관리 코드에 해당 하는 도구는 [ildasm.exe](/dotnet/framework/tools/ildasm-exe-il-disassembler)입니다.

[/Gl (전체 프로그램 최적화)](gl-whole-program-optimization.md) 컴파일러 옵션을 사용 하 여 생성 된 파일에는 [/svvvvvhhonly](headers.md) 옵션을 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[DUMPBIN 옵션](dumpbin-options.md)
