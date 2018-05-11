---
title: _crtDbgFlag | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _crtDbgFlag
- crtDbgFlag
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, tracking flag
- crtDbgFlag constant
- _crtDbgFlag constant
- debug heap, tracking memory on
- debug heap, control flags
- enable memory allocation tracking flag
- memory, tracking on the debug heap
ms.assetid: 9e7adb47-8ab9-4e19-81d5-e2f237979973
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb0c22e65c33ab8f689026e916f550280bf6a8ad
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="crtdbgflag"></a>_crtDbgFlag
**_crtDbgFlag** 플래그는 힙의 디버그 버전에서 메모리 할당을 추적, 확인, 보고 및 덤프하는 방법을 제어하는 비트 필드 5개로 구성됩니다. 플래그의 비트 필드는 [_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md) 함수를 사용하여 설정합니다. 이 플래그와 해당 비트 필드는 Crtdbg.h에서 선언됩니다. 이 플래그는 [_DEBUG](../c-runtime-library/debug.md) 플래그를 응용 프로그램에서 정의한 경우에만 사용할 수 있습니다.  
  
 다른 디버그 함수와 함께 이 플래그 사용에 대한 자세한 내용은 [힙 상태 보고 함수](/visualstudio/debugger/crt-debug-heap-details)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [제어 플래그](../c-runtime-library/control-flags.md)