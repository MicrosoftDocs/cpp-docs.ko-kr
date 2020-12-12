---
description: '자세한 정보: 컴파일러 오류 C3415'
title: 컴파일러 오류 C3415
ms.date: 11/04/2016
f1_keywords:
- C3415
helpviewer_keywords:
- C3415
ms.assetid: fa2db8ab-2820-4ec3-a740-fb5e2adcfb29
ms.openlocfilehash: 3f50f2bd7a443c01f820aa1915f14d83e0b0dbe8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321915"
---
# <a name="compiler-error-c3415"></a>컴파일러 오류 C3415

여러 'section_name' 섹션이 다양한 특성('value')을 갖고 있습니다.

[section](../../preprocessor/section.md) pragma에 충돌되는 값이 지정되었습니다.

`value` 는 ntimage.h에 지정된 것처럼 섹션의 현재 설정입니다. 예를 들어:

```
// Section contains extended relocations.
#define IMAGE_SCN_LNK_NRELOC_OVFL            0x01000000
// Section can be discarded.
#define IMAGE_SCN_MEM_DISCARDABLE            0x02000000
// Section is not cachable.
#define IMAGE_SCN_MEM_NOT_CACHED             0x04000000
// Section is not pageable.
#define IMAGE_SCN_MEM_NOT_PAGED              0x08000000
// Section is shareable.
#define IMAGE_SCN_MEM_SHARED                 0x10000000
// Section is executable.
#define IMAGE_SCN_MEM_EXECUTE                0x20000000
// Section is readable.
#define IMAGE_SCN_MEM_READ                   0x40000000
// Section is writeable.
#define IMAGE_SCN_MEM_WRITE                  0x80000000
```

다음 샘플에서는 C3415를 생성합니다.

```cpp
// C3415.cpp
#pragma section("mysec1",write)
#pragma section("mysec1",read)   // C3415
```
