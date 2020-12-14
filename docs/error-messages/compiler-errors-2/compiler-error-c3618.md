---
description: '자세한 정보: 컴파일러 오류 C3618'
title: 컴파일러 오류 C3618
ms.date: 11/04/2016
f1_keywords:
- C3618
helpviewer_keywords:
- C3618
ms.assetid: cacc105d-4389-4cb8-ae6c-41a3622e9a86
ms.openlocfilehash: 09e1a2a77410cc7836c00a3dd11cf5ed36553273
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223076"
---
# <a name="compiler-error-c3618"></a>컴파일러 오류 C3618

' function ': DllImport로 표시 된 메서드를 정의할 수 없습니다.

로 표시 된 메서드가 <xref:System.Runtime.InteropServices.DllImportAttribute> specified.DLL에 정의 되어 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3618를 생성 합니다.

```cpp
// C3618.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;

[ DllImport("user32.dll", EntryPoint="MessageBox", CharSet=CharSet::Ansi) ]  // CHANGED
void Func();

void Func() {}   // C3618, remove this function definition to resolve
```
