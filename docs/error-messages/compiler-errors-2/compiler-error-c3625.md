---
description: '자세한 정보: 컴파일러 오류 C3625'
title: 컴파일러 오류 C3625
ms.date: 11/04/2016
f1_keywords:
- C3625
helpviewer_keywords:
- C3625
ms.assetid: fdf49f21-d6b1-42f4-9eec-23b04ae8b4aa
ms.openlocfilehash: ee28175eac35e05ca2a4620dffa84cf995e053a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144497"
---
# <a name="compiler-error-c3625"></a>컴파일러 오류 C3625

'native_type': 네이티브 형식은 WinRT 또는 관리되는 형식 'type'에서 파생될 수 없습니다.

네이티브 클래스는 WinRT 또는 관리되는 클래스에서 상속할 수 없습니다. 자세한 내용은 [클래스 및 구조체](../../extensions/classes-and-structs-cpp-component-extensions.md)를 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3625 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C3625.cpp
// compile with: /clr /c
ref class B {};
class D : public B {};   // C3625 cannot inherit from a managed class
```
