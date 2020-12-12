---
description: '자세한 정보: 컴파일러 오류 C3809'
title: 컴파일러 오류 C3809
ms.date: 11/04/2016
f1_keywords:
- C3809
helpviewer_keywords:
- C3809
ms.assetid: 37eca584-c20c-464e-8e45-a987214b7ce4
ms.openlocfilehash: 62e7ff06e6ed5bf34861fdbae3f823e19ad5aad4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328209"
---
# <a name="compiler-error-c3809"></a>컴파일러 오류 C3809

'class': 관리되는 또는 WinRT 형식에 friend 함수/클래스/인터페이스를 사용할 수 없습니다.

관리 되는 형식 및 Windows 런타임 형식에서는 friend를 허용하지 않습니다. 이 오류를 해결하려면 관리되는 형식이나 Windows 런타임 형식 내에서 friend를 선언하지 마세요.

다음 샘플에서는 C3809를 생성합니다.

```cpp
// C3809a.cpp
// compile with: /clr
ref class A {};

ref class B
{
public:
   friend ref class A;   // C3809
};

int main()
{
}
```
