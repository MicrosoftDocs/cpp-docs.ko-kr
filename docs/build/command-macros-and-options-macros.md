---
title: 명령 매크로 옵션 매크로 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ab8b1d61c2c4f6ae9125b8eefaf05f791f57b259
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="command-macros-and-options-macros"></a>명령 매크로와 옵션 매크로
명령 매크로 Microsoft 제품에 대 한 미리 정의 합니다. 옵션 매크로 옵션 이러한 제품을 나타내고 기본적으로 정의 되어 있지 않습니다. 모두 미리 정의 된 규칙에 사용 되 고 설명 블록 또는 사용자 정의 유추 규칙에서 사용할 수 있습니다. 옵션을 포함 하는 명령줄의 일부 또는 전체를 나타내기 위해 명령 매크로 재정의할 수 있습니다. 옵션 매크로 정의 하지 않으면 null 문자열을 생성 합니다.  
  
|Microsoft 제품|명령 매크로|로 정의|옵션 매크로|  
|-----------------------|-------------------|----------------|-------------------|  
|매크로 어셈블러|**마찬가지로**|ml|**AFLAGS**|  
|기본 컴파일러|**BC**|bc|**BFLAGS**|  
|C 컴파일러|**참조**|Cl|**CFLAGS**|  
|C++ 컴파일러|**CPP**|Cl|**CPPFLAGS**|  
|C++ 컴파일러|**CXX**|Cl|**CXXFLAGS**|  
|리소스 컴파일러|**RC**|rc|**RFLAGS**|  
  
## <a name="see-also"></a>참고 항목  
 [특수 NMake 매크로](../build/special-nmake-macros.md)