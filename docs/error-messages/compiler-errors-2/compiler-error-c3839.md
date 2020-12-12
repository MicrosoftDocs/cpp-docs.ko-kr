---
description: '자세한 정보: 컴파일러 오류 C3839'
title: 컴파일러 오류 C3839
ms.date: 11/04/2016
f1_keywords:
- C3839
helpviewer_keywords:
- C3839
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
ms.openlocfilehash: 8b34cdd7f09bea924d3e184f7ea639c3f8210ed5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180801"
---
# <a name="compiler-error-c3839"></a>컴파일러 오류 C3839

관리되는 또는 WinRT 형식의 맞춤 방식을 변경할 수 없습니다.

관리 되는 형식 또는 Windows 런타임 형식의 변수 맞춤은 CLR 또는 Windows 런타임에 의해 제어 되며 [align](../../cpp/align-cpp.md)으로 수정할 수 없습니다.

다음 샘플에서는 C3839를 생성합니다.

```cpp
// C3839a.cpp
// compile with: /clr
ref class C
{
public:
   __declspec(align(32)) int m_j; // C3839
};

int main()
{
}
```
