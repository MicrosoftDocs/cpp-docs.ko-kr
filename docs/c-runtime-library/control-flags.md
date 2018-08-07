---
title: 제어 플래그 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.flags
dev_langs:
- C++
helpviewer_keywords:
- flags, control
- heap allocation, control flags
- debug heap, control flags
ms.assetid: 8dbd24a5-0633-42d1-9771-776db338465f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bfd37a3d76a39748efc0352df829a7b5c57146a9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32388288"
---
# <a name="control-flags"></a>제어 플래그
Microsoft C 런타임 라이브러리의 디버그 버전에서는 힙 할당과 보고 프로세스를 제어하기 위해 다음 플래그를 사용합니다. 자세한 내용은 [CRT 디버깅 기술](/visualstudio/debugger/crt-debugging-techniques)을 참조하세요.  
  
|플래그|설명|  
|----------|-----------------|  
|[_CRTDBG_MAP_ALLOC](../c-runtime-library/crtdbg-map-alloc.md)|기본 힙 함수를 디버그 버전 함수에 매핑합니다.|  
|[_DEBUG](../c-runtime-library/debug.md)|런타임 함수의 디버깅 버전을 사용할 수 있습니다.|  
|[_crtDbgFlag](../c-runtime-library/crtdbgflag.md)|디버그 힙 관리자가 할당을 추적하는 방법을 제어합니다.|  
  
 이러한 플래그는 /D 명령줄 옵션이나 `#define` 명령을 사용하여 정의될 수 있습니다. 플래그가 `#define`을 통해 정의되는 경우 지시문은 루틴 선언의 헤더 파일 include 문보다 앞에 위치해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [전역 변수 및 표준 형식](../c-runtime-library/global-variables-and-standard-types.md)