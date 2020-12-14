---
description: '자세한 정보: 컴파일러 오류 C3734'
title: 컴파일러 오류 C3734
ms.date: 11/04/2016
f1_keywords:
- C3734
helpviewer_keywords:
- C3734
ms.assetid: 4e2afdcc-7da9-45a1-9c96-85f25e2986e8
ms.openlocfilehash: f24c81c06a0e140f7970e8a6fc96d90aae3780f8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245007"
---
# <a name="compiler-error-c3734"></a>컴파일러 오류 C3734

'class': 관리되는 클래스 또는 WinRT 클래스에는 coclass를 사용할 수 없습니다.

[Coclass](../../windows/attributes/coclass.md) 특성은 관리 되는 클래스 또는 WinRT 클래스와 함께 사용할 수 없습니다.

다음 샘플에서는 C3734를 생성하고 해결 방법을 보여 줍니다.

```cpp
// C3734.cpp
// compile with: /clr /c
[module(name="x")];

[coclass]
ref class CMyClass {   // C3734 remove the ref keyword to resolve
};
```
