---
description: '자세한 정보: 컴파일러 오류 C2261'
title: 컴파일러 오류 C2261
ms.date: 11/04/2016
f1_keywords:
- C2261
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
ms.openlocfilehash: c5156a240696f9021613b54cf7013e9372a13b45
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134617"
---
# <a name="compiler-error-c2261"></a>컴파일러 오류 C2261

' string ': 어셈블리 참조가 잘못 되어 확인할 수 없습니다.

값이 잘못 되었습니다.

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 는 friend 어셈블리를 지정 하는 데 사용 됩니다. 예를 들어 a.dll를 friend 어셈블리로 b.dll 지정 하려는 경우 (a.dll): InternalsVisibleTo ("b")를 지정 합니다. 그러면 런타임에서는 b.dll a.dll (전용 형식 제외) 모든 항목에 액세스할 수 있습니다.

Friend 어셈블리를 지정할 때 올바른 구문에 대 한 자세한 내용은 [Friend 어셈블리 (c + +)](../../dotnet/friend-assemblies-cpp.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C2261를 생성 합니다.

```cpp
// C2261.cpp
// compile with: /clr /c
using namespace System::Runtime::CompilerServices;
[assembly: InternalsVisibleTo("a,a,a")];   // C2261
[assembly: InternalsVisibleTo("a.a")];   // OK
[assembly: InternalsVisibleTo("a")];   // OK
```
