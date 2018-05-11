---
title: 버퍼 조작 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.memory
dev_langs:
- C++
helpviewer_keywords:
- buffers, manipulation routines
- buffers
ms.assetid: 164f4860-ce66-412c-8291-396fbd70f03e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a7544dfa80ce0c7481846383dd812ce30b78290
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="buffer-manipulation"></a>버퍼 조작

다음 루틴을 사용하여 바이트 단위별로 메모리 영역을 사용할 수 있습니다.

## <a name="buffer-manipulation-routines"></a>버퍼 조작 루틴

|루틴에서 반환된 값|사용|
|-------------|---------|
|[_memccpy](../c-runtime-library/reference/memccpy.md)|제공된 문자 또는 지정된 수의 문자가 복사될 때까지 한 버퍼에서 다른 버퍼로 문자를 복사합니다.|
|[memchr, wmemchr](../c-runtime-library/reference/memchr-wmemchr.md)|지정된 문자 수 내에서 버퍼의 지정된 문자가 처음 나오는 경우에 대한 포인터를 반환합니다.|
|[memcmp, wmemcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|두 버퍼에서 지정한 개수의 문자를 비교합니다.|
|[memcpy, wmemcpy](../c-runtime-library/reference/memcpy-wmemcpy.md), [memcpy_s, wmemcpy_s](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|한 버퍼에서 지정된 개수의 문자를 다른 버퍼로 복사합니다.|
|[_memicmp, _memicmp_l](../c-runtime-library/reference/memicmp-memicmp-l.md)|대/소문자에 상관없이 두 버퍼에서 지정된 개수의 문자를 비교합니다.|
|[memmove, wmemmove](../c-runtime-library/reference/memmove-wmemmove.md),[memmove_s, wmemmove_s](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|한 버퍼에서 지정된 개수의 문자를 다른 버퍼로 복사합니다.|
|[memset, wmemset](../c-runtime-library/reference/memset-wmemset.md)|지정된 문자를 사용하여 버퍼에서 지정된 수의 바이트를 초기화합니다.|
|[_swab](../c-runtime-library/reference/swab.md)|데이터의 바이트를 교환하고 지정된 위치에 저장합니다.|

소스 및 대상 영역이 겹치는 경우 **memmove**만 전체 소스를 제대로 복사할 수 있습니다.

## <a name="see-also"></a>참고 항목

[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)
