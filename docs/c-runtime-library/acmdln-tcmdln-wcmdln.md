---
title: _acmdln, _tcmdln, _wcmdln | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wcmdln
- _acmdln
apilocation:
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _acmdln
- acmdln
- _wcmdln
- wcmdln
- _tcmdln
- tcmdln
dev_langs:
- C++
helpviewer_keywords:
- _wcmdln global variable
- wcmdln global variable
- _acmdln global variable
- _tcmdln global variable
- tcmdln global variable
- acmdln global variable
ms.assetid: 4fc0a6a0-3f93-420a-a19f-5276061ba539
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8250822adb801365fca826f33899a7ae3d1d06a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="acmdln-tcmdln-wcmdln"></a>_acmdln, _tcmdln, _wcmdln
내부 CRT 전역 변수입니다. 명령줄입니다.  
  
## <a name="syntax"></a>구문  
  
```  
char * _acmdln;  
wchar_t * _wcmdln;  
  
#ifdef WPRFLAG  
   #define _tcmdln _wcmdln  
#else  
   #define _tcmdln _acmdln  
```  
  
## <a name="remarks"></a>설명  
 이러한 CRT 내부 변수는 전체 명령줄을 저장하고 CRT의 내보낸 기호에 노출되지만 사용자 코드에 사용할 수는 없습니다. `_acmdln`은 데이터를 문자열로 저장합니다. `_wcmdln`은 데이터를 와이드 문자열로 저장합니다. `_tcmdln`은 어떤 것이 적절한지에 따라 `_acmdln` 또는 `_wcmdln`으로 정의할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [전역 변수](../c-runtime-library/global-variables.md)