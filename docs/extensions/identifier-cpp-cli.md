---
description: '자세한 정보: __identifier (c + +/CLI)'
title: __identifier(C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- __identifier
- __identifier_cpp
helpviewer_keywords:
- __identifier keyword [C++]
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
ms.openlocfilehash: 663d05ef482a97b4ac33664ab62f1556e62763a6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119098"
---
# <a name="__identifier-ccli"></a>__identifier(C++/CLI)

C++ 키워드를 식별자로 사용할 수 있습니다.

## <a name="all-platforms"></a>모든 플랫폼

### <a name="syntax"></a>구문

```cpp
__identifier(C++_keyword)
```

### <a name="remarks"></a>설명

키워드가 아닌 식별자에 **__identifier** 키워드를 사용할 수 있지만, 스타일상 사용하지 않는 것이 좋습니다.

## <a name="windows-runtime"></a>Windows 런타임

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

### <a name="examples"></a>예제

**예제**

다음 예제에서는 라는 클래스가 `template` c #에서 만들어지고 DLL로 배포 됩니다. 클래스를 사용 하는 c + +/CLI 프로그램에서 `template` **`__identifier`** 키워드는 `template` 표준 c + + 키워드인 팩트를 숨깁니다.

```csharp
// identifier_template.cs
// compile with: /target:library
public class template {
   public void Run() { }
}
```

```cpp
// keyword__identifier.cpp
// compile with: /ZW
#using <identifier_template.dll>
int main() {
   __identifier(template)^ pTemplate = ref new __identifier(template)();
   pTemplate->Run();
}
```

## <a name="common-language-runtime"></a>공용 언어 런타임

### <a name="remarks"></a>설명

**__identifier** 키워드는 `/clr` 컴파일러 옵션에서 유효합니다.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

### <a name="examples"></a>예제

다음 예제에서는 라는 클래스가 `template` c #에서 만들어지고 DLL로 배포 됩니다. 클래스를 사용 하는 c + +/CLI 프로그램에서 `template` **`__identifier`** 키워드는 `template` 표준 c + + 키워드인 팩트를 숨깁니다.

```csharp
// identifier_template.cs
// compile with: /target:library
public class template {
   public void Run() { }
}
```

```cpp
// keyword__identifier.cpp
// compile with: /clr
#using <identifier_template.dll>

int main() {
   __identifier(template) ^pTemplate = gcnew __identifier(template)();
   pTemplate->Run();
}
```

## <a name="see-also"></a>참고 항목

[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)<br/>
[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)
