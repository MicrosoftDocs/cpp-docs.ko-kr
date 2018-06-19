---
title: 컴파일러 경고 (수준 1) C4269 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4269
dev_langs:
- C++
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e393c657e12f84d3cadfacd469e35e3472a39d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281793"
---
# <a name="compiler-warning-level-1-c4269"></a>컴파일러 경고(수준 1) C4269
'identifier': 컴파일러에서 생성 된 기본 생성자를 사용 하 여 초기화 하는 'const' 자동 데이터 신뢰할 수 없는 결과 생성 합니다.  
  
 A **const** 특수 한 클래스의 자동 인스턴스는 컴파일러에서 생성 된 기본 생성자로 초기화 됩니다.  
  
## <a name="example"></a>예제  
  
```  
// C4269.cpp  
// compile with: /c /LD /W1  
class X {  
public:  
   int m_data;  
};  
  
void g() {  
   const X x1;   // C4269  
};  
```  
  
 클래스의이 인스턴스가 생성의 초기 값은 스택에 `m_data` 모두 사용할 수 있습니다. 또한 된는 **const** 인스턴스 값의 `m_data` 변경할 수 없습니다.