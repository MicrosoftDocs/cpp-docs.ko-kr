---
title: "컴파일러 오류 C2868 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2868
dev_langs:
- C++
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7255aa3e73e23109535ae0e83d6e9bd907cdbcd4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2868"></a>컴파일러 오류 C2868  
  
> '*식별자*': using 선언의 구문이 잘못 되었습니다; 정규화 된 이름이 필요 합니다.  
  
A [선언을 사용 하 여](../../cpp/using-declaration.md) 필요는 *정규화 된 이름*, 범위 연산자 (`::`) 식별자 이름으로 끝나는 네임 스페이스, 클래스 또는 열거형 이름의 시퀀스를 구분 합니다. 이름을 전역 네임 스페이스에서 제공 하는 단일 범위 결정 연산자를 사용할 수 있습니다.  
  
## <a name="example"></a>예  
  
다음 샘플에서는 C2868 오류가 발생 하 고 올바른 사용법을 보여 줍니다.  
  
```cpp  
// C2868.cpp  
class X {  
public:  
   int i;  
};  
  
class Y : X {  
public:  
   using X::i;   // OK  
};  
  
int main() {  
   using X;   // C2868  
}  
```