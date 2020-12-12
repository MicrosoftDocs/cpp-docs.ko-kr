---
description: '자세한 정보: 컴파일러 오류 C3807'
title: 컴파일러 오류 C3807
ms.date: 11/04/2016
f1_keywords:
- C3807
helpviewer_keywords:
- C3807
ms.assetid: 7e2b0aab-8c61-4e71-b9c1-fcaeb6a1b5ea
ms.openlocfilehash: ffa8b52b13ae7245b62cd5aa8d7fec9285754b73
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97260100"
---
# <a name="compiler-error-c3807"></a>컴파일러 오류 C3807

' type ': ComImport 특성이 있는 클래스는 ' type2 '에서 파생 될 수 없으며 인터페이스만 구현할 수 있습니다.

에서 파생 된 형식은 <xref:System.Runtime.InteropServices.ComImportAttribute> 인터페이스만 구현할 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3807를 생성 합니다.

```cpp
// C3807.cpp
// compile with: /clr /c
ref struct S {};
interface struct I {};

[System::Runtime::InteropServices::ComImportAttribute()]
ref struct S1 : S {};   // C3807
ref struct S2 : I {};
```
