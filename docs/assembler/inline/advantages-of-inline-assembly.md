---
title: 인라인 어셈블리의 장점 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- assembler [C++], advantages
- inline assembly [C++], about inline assembly
- inline assembly [C++], using
ms.assetid: 94364d97-faa7-4bdf-8473-570956986c51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 998ec5ff04911d3e476f0864f81f82b804969a82
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32051709"
---
# <a name="advantages-of-inline-assembly"></a>인라인 어셈블리의 장점
## <a name="microsoft-specific"></a>Microsoft 전용  
 인라인 어셈블러에는 별도의 어셈블리 및 링크 단계가 필요 없으므로 별도의 어셈블리보다 편리합니다. 범위에 속한 C 변수 또는 함수 이름을 인라인 어셈블리 코드에 사용할 수 있으므로 인라인 어셈블리 코드를 프로그램의 C 코드와 쉽게 통합할 수 있습니다. 어셈블리 코드는 C 또는 C++ 문과 인라인으로 혼합할 수 있으므로 C 또는 C++에서 어렵거나 불가능한 작업을 수행할 수 있습니다.  
  
 인라인 어셈블리의 용도는 다음과 같습니다.  
  
-   어셈블리 언어로 함수를 작성합니다.  
  
-   코드에서 속도가 중요한 섹션을 집중적으로 최적화합니다.  
  
-   장치 드라이버의 직접 하드웨어 액세스를 만듭니다.  
  
-   "naked" 호출의 프롤로그 및 에필로그 코드를 작성합니다.  
  
 인라인 어셈블리는 특수 목적 도구입니다. 응용 프로그램을 다른 컴퓨터로 이식하기 위해 별도의 모듈에 컴퓨터별 코드를 배치할 수 있습니다. 인라인 어셈블러는 MASM(Microsoft Macro Assembler)의 매크로 및 데이터 지시문을 일부만 지원하므로 이런 모듈에는 MASM을 사용하는 것이 더 편리할 수 있습니다.  
  
 **Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [인라인 어셈블러](../../assembler/inline/inline-assembler.md)