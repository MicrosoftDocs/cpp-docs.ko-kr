---
description: 자세한 내용은 _emit Pseudoinstruction을 (를) 확인 하세요.
title: _emit Pseudoinstruction
ms.date: 08/30/2018
f1_keywords:
- _emit
helpviewer_keywords:
- byte defining (inline assembly)
- _emit pseudoinstruction
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
ms.openlocfilehash: d3e2a39312c94ff0e4868bed9afa74011051a129
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117811"
---
# <a name="_emit-pseudoinstruction"></a>_emit Pseudoinstruction

**Microsoft 전용**

**_Emit** pseudoinstruction는 현재 텍스트 세그먼트의 현재 위치에서 1 바이트를 정의 합니다. **_Emit** PSEUDOINSTRUCTION는 MASM의 [DB](../../assembler/masm/db.md) 지시어와 비슷합니다.

다음 조각은 0x4A, 0x43, 0x4B 바이트를 코드에 추가합니다.

```cpp
#define randasm __asm _emit 0x4A __asm _emit 0x43 __asm _emit 0x4B
.
.
.
__asm {
    randasm
    }
```

> [!CAUTION]
> `_emit`이 레지스터를 수정하는 명령을 생성하는 경우 최적화 기능을 사용하여 애플리케이션을 컴파일하면 컴파일러는 영향을 받는 레지스터를 확인할 수 없습니다. 예를 들어가 `_emit` **rax** 레지스터를 수정 하는 명령을 생성 하는 경우 컴파일러는 **rax** 가 변경 되었음을 인식 하지 못합니다. 이 때문에 컴파일러는 인라인 어셈블러 코드가 실행된 후 해당 레지스터에 포함된 값을 잘못 가정할 수 있습니다. 따라서 애플리케이션이 실행될 때 예기치 않은 동작이 발생할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__Asm 블록에서 어셈블리 언어 사용](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
