---
title: ". 코드 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- .CODE
dev_langs:
- C++
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: de0a9b8930c04929b05b02931a1f796d28a78099
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="code"></a>.CODE
와 함께 사용할 경우 [합니다. 모델](../../assembler/masm/dot-model.md), 코드 세그먼트의 시작을 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
.CODE [[name]]  
```  
  
#### <a name="parameters"></a>매개 변수  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`name`|코드 세그먼트의 이름을 지정 하는 선택적 매개 변수입니다. 기본 이름은 아주 작은, 작은 압축 및 플랫에 대 한 _TEXT [모델](../../assembler/masm/dot-model.md)합니다. 기본 이름은 *modulename*_TEXT 다른 모델에 대 한 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [지시문 참조](../../assembler/masm/directives-reference.md)   
 [.DATA](../../assembler/masm/dot-data.md)