---
description: '자세한 정보: 컴파일러 오류 C3458'
title: 컴파일러 오류 C3458
ms.date: 11/04/2016
f1_keywords:
- C3458
helpviewer_keywords:
- C3458
ms.assetid: 940202fd-8dcc-4042-9c96-3f9e9127d2f1
ms.openlocfilehash: d26f252cfbbff21ac355a84aea6556d2c761b6d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315922"
---
# <a name="compiler-error-c3458"></a>컴파일러 오류 C3458

'attribute1': 'attribute2' 특성이 'construct'에 대해 이미 지정되어 있습니다.

함께 사용할 수 없는 두 특성이 동일한 구문에 대해 지정되었습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3458을 생성합니다.

```cpp
// C3458.cpp
// compile with: /clr /c
[System::Reflection::DefaultMember("Chars")]
public ref class MyString {
public:
   [System::Runtime::CompilerServices::IndexerName("Chars")]   // C3458
   property char default[int] {
      char get(int index);
      void set(int index, char c);
   }
};
```
