---
description: '자세한 정보: 컴파일러 오류 C3917'
title: 컴파일러 오류 C3917
ms.date: 11/04/2016
f1_keywords:
- C3917
helpviewer_keywords:
- C3917
ms.assetid: a24cd0c9-262f-46e5-9488-1c01f945933d
ms.openlocfilehash: 3e30e93f650e1b835aafd6639687560aa7349c1f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143938"
---
# <a name="compiler-error-c3917"></a>컴파일러 오류 C3917

'*property*': 사용 되지 않는 구문 선언 스타일입니다.

속성 또는 이벤트 정의는 Visual Studio 2005 이전 버전에서 구문을 사용 했습니다.

자세한 내용은 [property](../../extensions/property-cpp-component-extensions.md)을 참조하세요.

## <a name="example"></a>예제

```cpp
// C3917.cpp
// compile with: /clr /c
public ref class  C {
private:
   int m_length;
public:
   C() {
      m_length = 0;
   }

   property int get_Length();   // C3917

   // The correct property definition:
   property int Length {
      int get() {
         return m_length;
      }

      void set( int i ) {
         m_length = i;
      }
   }
};
```
