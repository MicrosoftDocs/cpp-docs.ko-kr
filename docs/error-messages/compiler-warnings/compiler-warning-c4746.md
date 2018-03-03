---
title: "컴파일러 경고 c 4746 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f92bae0e75d9a09de874cd999c044e703b3f3171
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-c4746"></a>컴파일러 경고 c 4746
volatile 액세스 '\<식 >' /volatile: [iso &#124; ms] 설정이 __iso_volatile_load/store 내장 함수를 사용 하 여 고려해 야 합니다.  
  
 C4746은 volatile 변수에 직접 액세스할 때마다 발생합니다. 현재 지정 된 특정 volatile 모델의 영향을 받는 코드 위치를 식별 하는 개발자가 하는 것 (으로 제어할 수 있습니다는 [/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) 컴파일러 옵션). 특히, /volatile:ms가 사용될 경우에는 컴파일러에서 생성된 하드웨어 메모리 장벽을 찾는데 유용할 수 있습니다.  
  
 __iso_volatile_load/store 내장 함수를 사용하면 volatile 모델의 영향을 받지 않고 volatile 메모리에 명시적으로 액세스할 수 있습니다. 이러한 내장 함수를 사용하면 C4746가 트리거되지 않습니다.  
  
 기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.