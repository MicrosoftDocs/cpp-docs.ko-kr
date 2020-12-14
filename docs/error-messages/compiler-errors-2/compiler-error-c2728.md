---
description: '자세한 정보: 컴파일러 오류 C2728'
title: 컴파일러 오류 C2728
ms.date: 11/04/2016
f1_keywords:
- C2728
helpviewer_keywords:
- C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
ms.openlocfilehash: 7ef24dd037f8d765c072a61320da64411248dbc1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245306"
---
# <a name="compiler-error-c2728"></a>컴파일러 오류 C2728

'type' : 네이티브 배열은 이러한 형식을 포함할 수 없습니다.

배열 생성 구문을 사용하여 관리되는 개체 또는 WinRT 개체를 만들었습니다. 관리되는 개체 또는 WinRT 개체의 배열은 네이티브 배열 구문을 사용하여 만들 수 없습니다.

자세한 내용은 [배열](../../extensions/arrays-cpp-component-extensions.md)을 참조하세요.

다음 샘플에서는 C2728 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C2728.cpp
// compile with: /clr

int main() {
   int^ arr[5];   // C2728

   // try the following line instead
   array<int>^arr2;
}
```
