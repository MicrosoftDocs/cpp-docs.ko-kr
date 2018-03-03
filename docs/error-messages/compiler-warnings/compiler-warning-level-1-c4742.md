---
title: "컴파일러 경고 (수준 1) C4742 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4742
dev_langs:
- C++
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: da12d4d1e5e8b6f9be6c21601e04f08d1b269cec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4742"></a>컴파일러 경고(수준 1) C4742
'var'에 'file1' 및 'file2'에서 서로 다른 맞춤: 번호와 번호  
  
 외부 변수가 참조 하거나 두 파일에 정의 된 해당 파일에 다른 맞춤을 있습니다. 이 경고는 컴파일러 있음을 발견 될 때 내보내집니다 `__alignof` 에서 변수의 *file1* 에서 다른 `__alignof` 에서 변수의 *file2*합니다. 다른 파일에서 변수를 선언 하는 경우 호환 되지 않는 형식을 사용 하 여 또는 일치 하지 않는 사용 하 여이 발생할 수 있습니다 `#pragma pack` 서로 다른 파일에 있습니다.  
  
 이 경고를 해결 하려면 같은 형식 정의 사용 하거나 변수에 대 한 서로 다른 이름을 사용 합니다.  
  
 자세한 내용은 참조 [팩](../../preprocessor/pack.md) 및 [__alignof 연산자](../../cpp/alignof-operator.md)합니다.  
  
## <a name="example"></a>예  
 형식을 정의 하는 첫 번째 파일입니다.  
  
```  
// C4742a.c  
// compile with: /c  
struct X {  
   char x, y, z, w;  
} global;  
```  
  
## <a name="example"></a>예  
 다음 샘플에서는 C4742 오류가 발생 합니다.  
  
```  
// C4742b.c  
// compile with: C4742a.c /W1 /GL  
// C4742 expected  
extern struct X {  
   int a;  
} global;  
  
int main() {  
   global.a = 0;  
}  
```