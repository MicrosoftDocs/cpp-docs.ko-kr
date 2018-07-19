---
title: 컴파일러 오류 C3292 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3292
dev_langs:
- C++
helpviewer_keywords:
- C3292
ms.assetid: ead485cc-5471-4e10-b361-300589ff5b70
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55a7f91bb9d47f2675525cf17096deddae30be71
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33248823"
---
# <a name="compiler-error-c3292"></a>컴파일러 오류 C3292
cli 네임스페이스를 다시 열 수 없습니다.  
  
 cli 네임스페이스를 코드에서 선언할 수 없습니다.  자세한 내용은 참조 [플랫폼, default 및 cli 네임 스페이스](../../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)합니다.  
  
## <a name="example"></a>예제  
 다음 샘플에서는 C3292를 생성합니다.  
  
```  
// C3292.cpp  
// compile with: /clr /c  
namespace cli {};   // C3292  
```