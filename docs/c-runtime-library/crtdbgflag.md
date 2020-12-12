---
description: '다음에 대 한 자세한 정보: _crtDbgFlag'
title: _crtDbgFlag
ms.date: 11/04/2016
f1_keywords:
- _crtDbgFlag
- crtDbgFlag
helpviewer_keywords:
- memory allocation, tracking flag
- crtDbgFlag constant
- _crtDbgFlag constant
- debug heap, tracking memory on
- debug heap, control flags
- enable memory allocation tracking flag
- memory, tracking on the debug heap
ms.assetid: 9e7adb47-8ab9-4e19-81d5-e2f237979973
ms.openlocfilehash: ef3c72b89ea9e5e557a567af9a9c52c8e85370ce
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97246762"
---
# <a name="_crtdbgflag"></a>_crtDbgFlag

**_crtDbgFlag** 플래그는 힙의 디버그 버전에서 메모리 할당을 추적, 확인, 보고 및 덤프하는 방법을 제어하는 비트 필드 5개로 구성됩니다. 플래그의 비트 필드는 [_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md) 함수를 사용하여 설정합니다. 이 플래그와 해당 비트 필드는 Crtdbg.h에서 선언됩니다. 이 플래그는 [_DEBUG](../c-runtime-library/debug.md) 플래그를 애플리케이션에서 정의한 경우에만 사용할 수 있습니다.

다른 디버그 함수와 함께 이 플래그 사용에 대한 자세한 내용은 [힙 상태 보고 함수](/visualstudio/debugger/crt-debug-heap-details)를 참조하세요.

## <a name="see-also"></a>참고 항목

[컨트롤 플래그](../c-runtime-library/control-flags.md)
