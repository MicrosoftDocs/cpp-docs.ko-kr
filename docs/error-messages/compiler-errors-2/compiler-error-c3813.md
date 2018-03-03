---
title: "컴파일러 오류 C3813 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3813
dev_langs:
- C++
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7462e4ab8975c089561356ba555b0a4a544880af
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3813"></a>컴파일러 오류 C3813
property 선언은 WinRT 또는 관리되는 형식의 정의 내에서만 사용할 수 있습니다.  
  
A [속성](../../dotnet/how-to-use-properties-in-cpp-cli.md) 으로만 관리 되는 또는 Windows 런타임 내에서 선언할 수 형식입니다. 네이티브 형식은 `property` 키워드를 지원하지 않습니다.  
  
## <a name="example"></a>예  
다음 샘플에서는 C3813 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.  
  
```cpp  
// C3813.cpp  
// compile by using: cl /c /clr C3813.cpp  
class A  
{  
   property int Int; // C3813  
};  
  
ref class B  
{  
   property int Int; // OK - declared within managed type  
};  
```