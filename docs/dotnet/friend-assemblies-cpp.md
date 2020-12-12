---
description: '자세한 정보: Friend 어셈블리 (c + +)'
title: Friend 어셈블리(C++)
ms.date: 11/04/2016
helpviewer_keywords:
- friend assemblies, Visual C++
ms.assetid: 8d55fee0-b7c2-4fbe-a23b-dfe424dc71cd
ms.openlocfilehash: 3f5a7dcd8833d6d396acfff5f42f6c1709327b2f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97252131"
---
# <a name="friend-assemblies-c"></a>Friend 어셈블리(C++)

적용 가능한 런타임의 경우 *friend 어셈블리* 언어 기능을 사용 하면 어셈블리 구성 요소에서 네임 스페이스 범위 또는 전역 범위에 있는 형식이 하나 이상의 클라이언트 어셈블리 또는. .netmodules에서 액세스할 수 있습니다.

## <a name="all-runtimes"></a>모든 런타임

**주의**

이 언어 기능은 모든 런타임에서 지원 되지 않습니다.

## <a name="windows-runtime"></a>Windows 런타임

**주의**

Windows 런타임에서는 이 언어 기능이 지원되지 않습니다.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: **/Zw**

## <a name="common-language-runtime"></a>공용 언어 런타임

**주의**

#### <a name="to-make-types-at-namespace-scope-or-global-scope-in-an-assembly-component-accessible-to-a-client-assembly-or-netmodule"></a>어셈블리 구성 요소에서 네임 스페이스 범위 또는 전역 범위에 있는 형식을 클라이언트 어셈블리 또는 .netmodule에서 액세스할 수 있도록 하려면

1. 구성 요소에서 어셈블리 특성 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 을 지정 하 고, 네임 스페이스 범위 또는 구성 요소의 전역 범위에서 형식에 액세스 하는 클라이언트 어셈블리 또는 .netmodule의 이름을 전달 합니다.  추가 특성을 지정 하 여 여러 클라이언트 어셈블리 또는. .netmodules을 지정할 수 있습니다.

1. 클라이언트 어셈블리 또는 .netmodule에서를 사용 하 여 구성 요소 어셈블리를 참조할 때 `#using` 특성을 전달 **`as_friend`** 합니다.  **`as_friend`** 을 지정 하지 않는 어셈블리에 대 한 특성을 지정 하는 경우 `InternalsVisibleToAttribute` 네임 스페이스 범위 또는 구성 요소의 전역 범위에서 형식에 액세스 하려고 하면 런타임 예외가 throw 됩니다.

특성을 포함 하는 어셈블리에 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 강력한 이름이 없지만 특성을 사용 하는 클라이언트 어셈블리의 경우 빌드 오류가 발생 **`as_friend`** 합니다.

네임 스페이스 범위 및 전역 범위의 형식은 클라이언트 어셈블리 또는 .netmodule에서 알 수 있지만 멤버 액세스 가능성은 여전히 적용 됩니다.  예를 들어 private 멤버에 액세스할 수 없습니다.

어셈블리의 모든 형식에 대 한 액세스를 명시적으로 부여 해야 합니다.  예를 들어, 어셈블리 c는 어셈블리 B를 참조 하 고 어셈블리 B는 어셈블리 A의 모든 형식에 액세스할 수 있는 경우 어셈블리 A의 모든 형식에 액세스할 수 없습니다.

에 강력한 이름을 지정 하는 방법, 즉 Microsoft c + + 컴파일러를 사용 하 여 빌드된 어셈블리를 서명 하는 방법에 대 한 자세한 내용은 [강력한 이름 어셈블리 (어셈블리 서명) (c + +/cli)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)를 참조 하세요.

Friend 어셈블리 기능을 사용 하는 대신를 사용 하 여 <xref:System.Security.Permissions.StrongNameIdentityPermission> 개별 형식에 대 한 액세스를 제한할 수 있습니다.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: **/clr**

### <a name="examples"></a>예제

다음 코드 예제에서는 구성 요소의 형식에 대 한 액세스 권한이 있는 클라이언트 어셈블리를 지정 하는 구성 요소를 정의 합니다.

```cpp
// friend_assemblies.cpp
// compile by using: /clr /LD
using namespace System::Runtime::CompilerServices;
using namespace System;
// an assembly attribute, not bound to a type
[assembly:InternalsVisibleTo("friend_assemblies_2")];

ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

다음 코드 예제에서는 구성 요소의 전용 형식에 액세스 합니다.

```cpp
// friend_assemblies_2.cpp
// compile by using: /clr
#using "friend_assemblies.dll" as_friend

int main() {
   Class1 ^ a = gcnew Class1;
   a->Test_Public();
}
```

```Output
Class1::Test_Public
```

다음 코드 예제에서는 구성 요소를 정의 하지만 구성 요소의 형식에 액세스할 수 있는 클라이언트 어셈블리를 지정 하지 않습니다.

구성 요소는 **/opt: 없음 ef** 를 사용 하 여 연결 됩니다. 이렇게 하면 특성이 있을 때 필요 하지 않은 구성 요소의 메타 데이터에서 전용 형식을 내보냅니다 `InternalsVisibleTo` . 자세한 내용은 [/OPT(최적화)](../build/reference/opt-optimizations.md)를 참조하세요.

```cpp
// friend_assemblies_3.cpp
// compile by using: /clr /LD /link /opt:noref
using namespace System;

ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

다음 코드 예제에서는 개인 형식에 대 한 액세스를 제공 하지 않는 구성 요소의 전용 형식에 액세스를 시도 하는 클라이언트를 정의 합니다. 런타임 동작으로 인해 예외를 catch 하려는 경우 도우미 함수에서 전용 형식에 액세스를 시도 해야 합니다.

```cpp
// friend_assemblies_4.cpp
// compile by using: /clr
#using "friend_assemblies_3.dll" as_friend
using namespace System;

void Test() {
   Class1 ^ a = gcnew Class1;
}

int main() {
   // to catch this kind of exception, use a helper function
   try {
      Test();
   }
   catch(MethodAccessException ^ e) {
      Console::WriteLine("caught an exception");
   }
}
```

```Output
caught an exception
```

다음 코드 예제에서는 구성 요소의 형식에 액세스할 수 있는 클라이언트 어셈블리를 지정 하는 강력한 이름 구성 요소를 만드는 방법을 보여 줍니다.

```cpp
// friend_assemblies_5.cpp
// compile by using: /clr /LD /link /keyfile:friend_assemblies.snk
using namespace System::Runtime::CompilerServices;
using namespace System;
// an assembly attribute, not bound to a type

[assembly:InternalsVisibleTo("friend_assemblies_6, PublicKey=00240000048000009400000006020000002400005253413100040000010001000bf45d77fd991f3bff0ef51af48a12d35699e04616f27ba561195a69ebd3449c345389dc9603d65be8cd1987bc7ea48bdda35ac7d57d3d82c666b7fc1a5b79836d139ef0ac8c4e715434211660f481612771a9f7059b9b742c3d8af00e01716ed4b872e6f1be0e94863eb5745224f0deaba5b137624d7049b6f2d87fba639fc5")];

private ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

구성 요소는 해당 공개 키를 지정 해야 합니다. 명령 프롬프트에서 다음 명령을 순서 대로 실행 하 여 키 쌍을 만들고 공개 키를 가져오는 것이 좋습니다.

**sn-d friend_assemblies .snk**

**sn-k friend_assemblies .snk**

**sn-i friend_assemblies .snk friend_assemblies**

**sn-pc friend_assemblies .snk 키. publickey**

**sn -tp key.publickey**

다음 코드 예제에서는 강력한 이름 구성 요소에서 전용 형식에 액세스 합니다.

```cpp
// friend_assemblies_6.cpp
// compile by using: /clr /link /keyfile:friend_assemblies.snk
#using "friend_assemblies_5.dll" as_friend

int main() {
   Class1 ^ a = gcnew Class1;
   a->Test_Public();
}
```

```Output
Class1::Test_Public
```

## <a name="see-also"></a>참고 항목

[런타임 플랫폼용 구성 요소 확장](../extensions/component-extensions-for-runtime-platforms.md)
