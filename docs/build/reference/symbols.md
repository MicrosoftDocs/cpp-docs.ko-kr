---
description: 자세히 알아보기:/SYMBOLS
title: /SYMBOLS
ms.date: 09/05/2018
f1_keywords:
- /symbols
helpviewer_keywords:
- symbols, dumping
- public symbols
- symbols, displaying COFF symbol table
- symbol tables
- SYMBOLS dumpbin option
- /SYMBOLS dumpbin option
- -SYMBOLS dumpbin option
ms.assetid: 34bcae90-4561-4c77-a80c-065508dec39a
ms.openlocfilehash: f0cc213a8b37f99e0cb80f6df88967e4eb5204b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230148"
---
# <a name="symbols"></a>/SYMBOLS

```
/SYMBOLS
```

이 옵션은 COFF 기호 테이블을 표시 합니다. 모든 개체 파일에 기호 테이블이 있습니다. . 줄이거나/DEBUG와 연결 된 경우에만 이미지 파일에 COFF 기호 테이블이 표시 됩니다.

다음은/기호에 대 한 출력에 대 한 설명입니다. /SYMBOLS 출력의 의미에 대 한 추가 정보는 winnt.exe (IMAGE_SYMBOL 및 IMAGE_AUX_SYMBOL) 또는 COFF 설명서를 참조 하 여 찾을 수 있습니다.

다음 샘플 덤프를 제공 합니다.

```
Dump of file main.obj
File Type: COFF OBJECT

COFF SYMBOL TABLE
000 00000000 DEBUG    notype       Filename     | .file
    main.cpp
002 000B1FDB ABS      notype       Static       | @comp.id
003 00000000 SECT1    notype       Static       | .drectve
    Section length     26, #relocs    0, #linenums    0, checksum 722C964F
005 00000000 SECT2    notype       Static       | .text
    Section length     23, #relocs    1, #linenums    0, checksum 459FF65F, selection    1 (pick no duplicates)
007 00000000 SECT2    notype ()    External     | _main
008 00000000 UNDEF    notype ()    External     | ?MyDump@@YAXXZ (void __cdecl MyDump(void))

String Table Size = 0x10 bytes

  Summary

         26 .drectve
         23 .text
```

## <a name="remarks"></a>설명

기호 번호로 시작 하는 줄에 대 한 다음 설명은 사용자와 관련 된 정보가 있는 열을 설명 합니다.

- 처음 3 자리 숫자는 기호 인덱스/숫자입니다.

- 세 번째 열에 섹션 *x* 가 포함 되어 있으면 개체 파일의 해당 섹션에 기호가 정의 됩니다. 그러나 UNDEF가 표시 되 면 해당 개체에 정의 되어 있지 않으며 다른 위치에서 확인 되어야 합니다.

- 다섯 번째 열 (Static, External)은 해당 개체 내 에서만 기호를 표시할지 또는 public (외부적으로 표시 됨) 인지를 알려 줍니다. 정적 기호 _sym는 공용 기호 _sym에 연결 되지 않습니다. 이는 _sym 이라는 두 가지 함수의 두 가지 인스턴스입니다.

번호가 매겨진 줄의 마지막 열은 데코 레이트 되지 않은 기호 이름입니다.

[/GL](gl-whole-program-optimization.md) 컴파일러 옵션으로 생성된 파일에서는 [/HEADERS](headers.md) DUMPBIN옵션만 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[DUMPBIN 옵션](dumpbin-options.md)
