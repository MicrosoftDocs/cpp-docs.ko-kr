---
title: 링커 도구 경고 LNK4254 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4254
dev_langs:
- C++
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb57882ab4269c06a53ed73fed2a9d6caf2f2c85
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33316896"
---
# <a name="linker-tools-warning-lnk4254"></a>링커 도구 경고 LNK4254
'사항 구역 1' 섹션 (오프셋) 'section2'에 병합 (오프셋) 다양 한 특성  
  
 하나의 섹션의 내용을 다른으로 병합 된 하지만 두 섹션의 특성 다릅니다. 프로그램에 예기치 않은 결과가 발생할 수 있습니다. 예를 들어 데이터를 읽으려면 수만 될 수 있습니다 이제 쓰기 가능한 섹션.  
  
 LNK4254를 해결 하려면 수정 하거나 병합 요청을 제거 합니다.  
  
 X86 대상으로 할 때 컴퓨터와 Visual c + +로 Windows CE 대상 (예: ARM, MIPS, SH4, 및 Thumb)는입니다. CRT 섹션은 읽기 전용입니다. 이전 동작에 종속 되는 코드 (합니다. CRT 섹션은 읽기/쓰기), 예기치 않은 동작이 수행 될 수 있습니다.  
  
 자세한 내용은 다음 항목을 참조하세요.  
  
-   [/MERGE(섹션 결합)](../../build/reference/merge-combine-sections.md)  
  
-   [C 주석(C/C++)](../../preprocessor/comment-c-cpp.md)  
  
## <a name="example"></a>예제  
 다음 샘플에서는 LNK4254 경고가 발생 합니다.  
  
```  
// LNK4254.cpp  
// compile with: /W1 /link /WX  
// LNK4254 expected  
#pragma comment(linker, "/merge:.data=.text")  
int main() {}  
```