---
title: 컴파일러 오류 C2452 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2452
dev_langs:
- C++
helpviewer_keywords:
- C2452
ms.assetid: a4ec7642-6660-4c7a-9866-853d1cc67daf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f4d30de808600c34270c8576adb371497af169aa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197223"
---
# <a name="compiler-error-c2452"></a>컴파일러 오류 C2452
'type': safe_cast의 잘못 된 원본 유형  
  
 소스 형식에 대 한 [safe_cast](../../windows/safe-cast-cpp-component-extensions.md) 올바르지 않습니다.  예를 들어 모든 형식에는 `safe_cast` 작업에는 CLR 형식 이어야 합니다.  
  
 다음 샘플에서는 C2452 오류가 생성 됩니다.  
  
```  
// C2452.cpp  
// compile with: /clr  
  
struct A {};  
struct B : public A {};  
  
ref struct C {};  
ref struct D : public C{};  
  
int main() {  
   A a;  
   safe_cast<B*>(&a);   // C2452  
  
   // OK  
   C ^ c = gcnew C;  
   safe_cast<D^>(c);  
}  
```