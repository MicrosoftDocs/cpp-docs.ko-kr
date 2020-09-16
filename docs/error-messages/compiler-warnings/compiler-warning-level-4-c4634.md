---
title: 컴파일러 경고(수준 4) C4634
ms.date: 11/04/2016
f1_keywords:
- C4634
helpviewer_keywords:
- C4634
ms.assetid: 3e3496ce-2ac7-43d0-a48a-f514c950e81d
ms.openlocfilehash: 86ac95fbd030ecf35a85eba153a449511ee7a535
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90683886"
---
# <a name="compiler-warning-level-4-c4634"></a>컴파일러 경고(수준 4) C4634

XML 문서 주석: 적용할 수 없습니다. reason

일부 C++ 구문에 XML 문서 태그를 적용할 수 없습니다.  예를 들어 네임스페이스 또는 템플릿에 문서 주석을 추가할 수 없습니다.

자세한 내용은 [XML Documentation](../../build/reference/xml-documentation-visual-cpp.md)을 참조하세요.

## <a name="examples"></a>예제

다음 샘플에서는 C4634를 생성합니다.

```cpp
// C4634.cpp
// compile with: /W4 /doc /c
/// This is a namespace.   // C4634
namespace hello {
   class MyClass  {};
};
```

다음 샘플에서는 C4634를 생성합니다.

```cpp
// C4634_b.cpp
// compile with: /W4 /doc /c
/// This is a template.   // C4634
template <class T>
class MyClass  {};
```
