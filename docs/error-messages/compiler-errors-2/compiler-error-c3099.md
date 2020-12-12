---
description: '자세한 정보: 컴파일러 오류 C3099'
title: 컴파일러 오류 C3099
ms.date: 11/04/2016
f1_keywords:
- C3099
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
ms.openlocfilehash: d065edd58df1e9196dc6aa31cfd4fb263f062f1d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116225"
---
# <a name="compiler-error-c3099"></a>컴파일러 오류 C3099

'keyword': 관리되는 특성에 대해 [System::AttributeUsageAttribute]를 사용하고, WinRT 특성에 대해 [Windows::Foundation::Metadata::AttributeUsageAttribute]를 사용합니다.

<xref:System.AttributeUsageAttribute>를 사용 하 여 **/clr** 특성을 선언 합니다. `Windows::Foundation::Metadata::AttributeUsageAttribute`를 사용하여 Windows 런타임 특성을 선언합니다.

/CLR 특성에 대 한 자세한 내용은 [사용자 정의 특성](../../extensions/user-defined-attributes-cpp-component-extensions.md)을 참조 하세요. Windows 런타임에서 지원 되는 특성은 [Windows Foundation. Metadata 네임 스페이스](/uwp/api/windows.foundation.metadata) 를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3099 오류가 발생하는 경우 및 이를 해결하는 방법을 보여 줍니다.

```cpp
// C3099.cpp
// compile with: /clr /c
using namespace System;
[usage(10)]   // C3099
// try the following line instead
// [AttributeUsageAttribute(AttributeTargets::All)]
ref class A : Attribute {};
```
