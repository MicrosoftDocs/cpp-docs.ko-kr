---
description: '다음에 대 한 자세한 정보: _CRTDBG_MAP_ALLOC'
title: _CRTDBG_MAP_ALLOC
ms.date: 11/04/2016
f1_keywords:
- CRTDBG_MAP_ALLOC
- _CRTDBG_MAP_ALLOC
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- memory allocation, in debug builds
- CRTDBG_MAP_ALLOC macro
ms.assetid: 435242b8-caea-4063-b765-4a608200312b
ms.openlocfilehash: e2747f6da04c019b551e68c78f6f1448c48093f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224272"
---
# <a name="_crtdbg_map_alloc"></a>_CRTDBG_MAP_ALLOC

**_CRTDBG_MAP_ALLOC** 플래그가 애플리케이션의 디버그 버전에서 정의된 경우 기본 버전의 힙 함수는 해당 디버그 버전에 직접 매핑됩니다. 이 플래그는 매핑을 수행하기 위해 Crtdbg.h에서 사용됩니다. 이 플래그는 [_DEBUG](../c-runtime-library/debug.md) 플래그를 애플리케이션에서 정의한 경우에만 사용할 수 있습니다.

힙 함수의 디버그 버전과 기본 버전을 사용하는 방법에 대한 자세한 내용은 [디버그 버전 및 기본 버전 사용](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)을 참조하세요.

## <a name="see-also"></a>참고 항목

[컨트롤 플래그](../c-runtime-library/control-flags.md)
