---
title: "열거형 (C + + /cli CX) | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b3a95af557dd416d99368dbd1ab51495e0bd1d85
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="enums-ccx"></a>열거형(C++/CX)
C + + /cli CX 지원는 `public enum class` 키워드는 표준 c + +과 유사한 `scoped  enum`합니다. `public enum class` 키워드를 사용하여 선언된 열거자를 사용할 경우 열거형 식별자를 사용하여 각 열거자 값의 범위를 지정해야 합니다.  
  
### <a name="remarks"></a>설명  
 `public enum class` 과 같은 액세스 지정자가 없는 `public`는 표준 C++ [범위 지정 열거형](../cpp/enumerations-cpp.md)으로 처리됩니다.  
  
 A `public enum class` 또는 `public enum struct` 자체는 Windows 런타임에서 형식이 int32 또는 uint32 플래그 열거형 되어야 한다는 필요로 하지만 선언은 내부 형식이 모든 정수 계열 형식일을 가질 수 있습니다. 다음 구문에서는 `public enum class` 또는 `public enum struct`부분을 설명합니다.  
  
 이 예제에서는 public enum 클래스를 정의하는 방법을 보여 줍니다.  
  
 [!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]  
  
 다음 예제에서는 클래스를 사용하는 방법을 보여 줍니다.  
  
 [!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]  
  
### <a name="examples"></a>예제  
 다음 예제에서는 열거형을 선언하는 방법을 보여 줍니다.  
  
 [!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]  
  
 다음 예제에서는 해당 숫자로 캐스팅하고 비교를 수행하는 방법을 보여 줍니다. 열거자 `One` 의 사용은 `Enum1` 열거형 식별자로 범위가 지정되고, 열거자 `First` 는 `Enum2`로 범위가 지정됩니다.  
  
 [!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]  
  
## <a name="see-also"></a>참고 항목  
 [형식 시스템](../cppcx/type-system-c-cx.md)   
 [Visual c + + 언어 참조](../cppcx/visual-c-language-reference-c-cx.md)   
 [네임 스페이스 참조](../cppcx/namespaces-reference-c-cx.md)