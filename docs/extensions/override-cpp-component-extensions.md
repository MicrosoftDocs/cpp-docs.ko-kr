---
description: '자세히 알아보기: override (c + +/CLI 및 c + +/CX)'
title: override  (C++/CLI 및 C++/CX)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- overriding, override keyword [C++]
- override keyword [C++]
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
ms.openlocfilehash: 1be49ac9b9e2d0f2eb3342855a42e9707f883078
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335939"
---
# <a name="override--ccli-and-ccx"></a>override  (C++/CLI 및 C++/CX)

**override** 상황에 맞는 키워드는 형식의 멤버가 기본 클래스 또는 기본 인터페이스 멤버를 재정의함을 나타냅니다.

## <a name="remarks"></a>설명

**override** 키워드는 네이티브 대상(기본 컴파일러 옵션), Windows 런타임 대상(`/ZW` 컴파일러 옵션) 또는 공용 언어 런타임 대상(`/clr` 컴파일러 옵션)에 대해 컴파일할 때 유효합니다.

override 지정자에 대한 자세한 내용은 [override 지정자](../cpp/override-specifier.md)와 [override 지정자 및 네이티브 컴파일](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)을 참조하세요.

상황에 맞는 키워드에 대한 자세한 내용은 [상황에 맞는 키워드](context-sensitive-keywords-cpp-component-extensions.md)를 참조하세요.

## <a name="examples"></a>예제

다음 코드 예제에서는 네이티브 컴파일에도 **override** 를 사용할 수 있음을 보여 줍니다.

```cpp
// override_keyword_1.cpp
// compile with: /c
struct I1 {
   virtual void f();
};

struct X : public I1 {
   virtual void f() override {}
};
```

### <a name="example"></a>예제

다음 코드 예제에서는 Windows 런타임 컴파일에 **override** 를 사용할 수 있음을 보여 줍니다.

```cpp
// override_keyword_2.cpp
// compile with: /ZW /c
ref struct I1 {
   virtual void f();
};

ref struct X : public I1 {
   virtual void f() override {}
};
```

#### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

### <a name="example"></a>예제

다음 코드 예제에서는 공용 언어 런타임 컴파일에 **override** 를 사용할 수 있음을 보여 줍니다.

```cpp
// override_keyword_3.cpp
// compile with: /clr /c
ref struct I1 {
   virtual void f();
};

ref struct X : public I1 {
   virtual void f() override {}
};
```

#### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

## <a name="see-also"></a>참고 항목

[override 지정자](../cpp/override-specifier.md)<br/>
[Override 지정자](override-specifiers-cpp-component-extensions.md)
