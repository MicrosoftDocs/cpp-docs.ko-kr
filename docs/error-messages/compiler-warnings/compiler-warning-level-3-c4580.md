---
title: 컴파일러 경고(수준 3) C4580
ms.date: 11/04/2016
f1_keywords:
- C4580
helpviewer_keywords:
- C4580
ms.assetid: fef6e8e0-0d6a-44fa-b22a-2fe7ba2ef379
ms.openlocfilehash: bd2ecff5adc6538f75c61772b785acbfc89092ae
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776862"
---
# <a name="compiler-warning-level-3-c4580"></a>컴파일러 경고(수준 3) C4580

[attribute]는 사용되지 않습니다. 대신 System::Attribute or Platform::Metadata를 기본 클래스로 지정합니다.

[[특성](../../windows/attributes/attribute.md)] 사용자 정의 특성을 만들기 위한 기본 구문은 더 이상. 자세한 내용은 [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md)을 참조하세요. CLR 코드의 경우 `System::Attribute`에서 특성을 파생시킵니다. Windows 런타임 코드의 경우 `Platform::Metadata`에서 특성을 파생시킵니다.

## <a name="example"></a>예제

다음 샘플에서는 C3454 오류가 발생하는 경우 및 이를 해결 방법을 보여 줍니다.

```cpp
// C4580.cpp
// compile with: /W3 /c /clr
[attribute]   // C4580
public ref class Attr {
public:
   int m_t;
};

public ref class Attr2 : System::Attribute {
public:
   int m_t;
};
```