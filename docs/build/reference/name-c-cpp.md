---
title: "이름 (C/C + +) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- name
dev_langs:
- C++
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 33e81f63e7647cbdbdc89b37ffdcb309b79e9340
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="name-cc"></a>NAME(C/C++)
기본 출력 파일에 대 한 이름을 지정합니다.  
  
```  
NAME [application][BASE=address]  
```  
  
## <a name="remarks"></a>설명  
 출력 파일 이름을 지정 하는 해당 하는 방법은 [/out](../../build/reference/out-output-file-name.md) 링커 옵션 및 기본 주소를 설정 하는 해당 하는 방법에 됩니다는 [/base](../../build/reference/base-base-address.md) 링커 옵션입니다. 둘 다 지정 하면 아웃 재정의 / **이름**합니다.  
  
 DLL을 작성 하는 경우 이름 DLL 이름에만 적용 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [모듈 정의 문의 규칙](../../build/reference/rules-for-module-definition-statements.md)