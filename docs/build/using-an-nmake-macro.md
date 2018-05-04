---
title: NMAKE 매크로 사용 하 여 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- NMAKE macros, using
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6bf098a3723aa7b067b8192bf503975998e4e98
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="using-an-nmake-macro"></a>NMAKE 매크로 사용
매크로 사용 하려면 해당 이름을 앞에 달러 기호 ($)에 다음과 같이 괄호로 묶습니다.  
  
## <a name="syntax"></a>구문  
  
```  
$(macroname)  
```  
  
## <a name="remarks"></a>설명  
 공백이 있어서는 안 됩니다. 괄호를 사용할 경우 *매크로 이름* 는 단일 문자입니다. 정의 문자열 대체 $(*매크로 이름*); null 문자열에 의해 정의 되지 않은 매크로 대체 됩니다.  
  
## <a name="what-do-you-want-to-know-more-about"></a>추가 정보  
 [매크로 대체](../build/macro-substitution.md)  
  
## <a name="see-also"></a>참고 항목  
 [매크로와 NMake](../build/macros-and-nmake.md)