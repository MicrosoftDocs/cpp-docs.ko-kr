---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4397'
title: 컴파일러 경고(수준 1) C4397
ms.date: 11/04/2016
f1_keywords:
- C4397
helpviewer_keywords:
- C4397
ms.assetid: 6346fdc2-dbbf-4fba-803a-32b0d0a707be
ms.openlocfilehash: 17ad322980a199b9602c4aa1ea60d818e657eaa1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311255"
---
# <a name="compiler-warning-level-1-c4397"></a>컴파일러 경고(수준 1) C4397

System.runtime.interopservices.defaultcharsetattribute은 무시 됩니다.

<xref:System.Runtime.InteropServices.DefaultCharSetAttribute> 는 Microsoft c + + 컴파일러에서 무시 됩니다. DLL에 대 한 문자 집합을 지정 하려면 DllImport의 CharSet 옵션을 사용 합니다. 자세한 내용은 [c + + Interop 사용 (암시적 PInvoke)](../../dotnet/using-cpp-interop-implicit-pinvoke.md)을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4397를 생성 합니다.

```cpp
// C4397.cpp
// compile with: /W1 /c /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[module:DefaultCharSetAttribute(CharSet::Unicode)];   // C4397

[DllImport("kernel32", EntryPoint="CloseHandle", CharSet=CharSet::Unicode)]   // OK
extern "C" bool ImportDefault(IntPtr hObject);

public ref class MySettingVC {
public:
   void method() {
      ImportDefault(IntPtr::Zero);
   }
};

[StructLayout(LayoutKind::Explicit)]
public ref struct StructDefault1{};

public ref class ClassDefault1{};
```
