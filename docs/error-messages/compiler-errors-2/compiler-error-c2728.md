---
title: "컴파일러 오류 C2728 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2728
dev_langs:
- C++
helpviewer_keywords:
- C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4574d3ffe02ea019a758f5b776279ea042e64697
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2728"></a>컴파일러 오류 C2728
'type' : 네이티브 배열은 이러한 형식을 포함할 수 없습니다.  
  
 배열 생성 구문을 사용하여 관리되는 개체 또는 WinRT 개체를 만들었습니다. 관리되는 개체 또는 WinRT 개체의 배열은 네이티브 배열 구문을 사용하여 만들 수 없습니다.  
  
 자세한 내용은 [배열](../../windows/arrays-cpp-component-extensions.md)을 참조하세요.  
  
 다음 샘플에서는 C2728 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.  
  
```  
// C2728.cpp  
// compile with: /clr  
  
int main() {  
   int^ arr[5];   // C2728  
  
   // try the following line instead  
   array<int>^arr2;  
}  
```  
