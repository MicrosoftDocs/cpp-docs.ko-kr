---
description: '자세한 정보: c + + Interop 사용 (암시적 PInvoke)'
title: C++ Interop 사용(암시적 PInvoke)
ms.date: 11/04/2016
helpviewer_keywords:
- blittable types [C++]
- platform invoke [C++], implicit
- interop [C++], features
- data marshaling [C++], C++ Interop features
- porting [C++], C++ native to .NET
- COM interfaces [C++]
- implicit platform invoke
- examples [C++], interoperability
- types [C++], blittable
- marshaling [C++], C++ Interop features
- platform invoke [C++], examples
- interoperability [C++]
- C++ Interop
- interoperability [C++], Implicit PInvoke
- C++, interop
- C++ COM Interop
- .NET [C++], porting C++ native to
ms.assetid: 5f710bf1-88ae-4c4e-8326-b3f0b7c4c68a
ms.openlocfilehash: e2b1f1aeef68fd6329ef04a53249d7dce627f2c5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255550"
---
# <a name="using-c-interop-implicit-pinvoke"></a>C++ Interop 사용(암시적 PInvoke)

다른 .NET 언어와 달리 Visual C++에는 관리 코드와 비관리 코드가 동일한 응용 프로그램에 존재 하 고 관리 되는 관리 [되지 않는](../preprocessor/managed-unmanaged.md) pragma를 사용 하 여 동일한 파일에 있을 수 있도록 하는 상호 운용성 지원이 있습니다. 이를 통해 개발자는 응용 프로그램의 나머지 부분을 중단시 키 지 않고 .NET 기능을 기존 Visual C++ 응용 프로그램에 통합할 Visual C++ 수 있습니다.

[Dllexport, dllimport를](../cpp/dllexport-dllimport.md)사용 하 여 관리 되는 compiland에서 관리 되지 않는 함수를 호출할 수도 있습니다.

암시적 PInvoke는 함수 매개 변수를 마샬링하는 방법을 지정 하지 않거나 명시적으로 S y s를 호출할 때 지정할 수 있는 기타 세부 정보를 지정할 필요가 없는 경우에 유용 합니다.

Visual C++는 관리 및 관리 되지 않는 함수를 상호 운용 하는 두 가지 방법을 제공 합니다.

- [C + +에서 명시적 PInvoke 사용 (DllImport 특성)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

명시적 PInvoke는 .NET Framework에서 지원 되며 대부분의 .NET 언어에서 사용할 수 있습니다. 그러나 이름에서 알 수 있듯이 c + + Interop는 Visual C++에만 해당 됩니다.

## <a name="c-interop"></a>C++ Interop

C + + Interop는 더 나은 형식 안전성을 제공 하므로 일반적으로를 구현 하는 것이 더 번거로울 수 있습니다. 그러나 관리 되지 않는 소스 코드를 사용할 수 없거나 플랫폼 간 프로젝트의 경우 c + + Interop는 옵션이 아닙니다.

## <a name="c-com-interop"></a>C++ COM Interop

Visual C++에서 지 원하는 상호 운용성 기능은 COM 구성 요소와 상호 운용 될 때 다른 .NET 언어에 비해 특정 이점을 제공 합니다. 데이터 형식에 대 한 제한 된 지원, 모든 COM 인터페이스의 모든 멤버에 대 한 필수 노출을 비롯 하 여 .NET Framework [Tlbimp.exe (형식 라이브러리 가져오기)](/dotnet/framework/tools/tlbimp-exe-type-library-importer)의 제한 사항으로 제한 되는 대신 c + + Interop를 사용 하면 com 구성 요소에 액세스할 수 있으며 별도의 Interop 어셈블리가 필요 하지 않습니다. Visual Basic 및 c #과 달리 Visual C++는 일반적인 COM 메커니즘 (예: **CoCreateInstance** 및 **QueryInterface**)을 사용 하 여 com 개체를 직접 사용할 수 있습니다. 이는 컴파일러에서 전환 코드를 자동으로 삽입 하 여 관리 되는 함수에서 관리 되지 않는 함수로 이동 하 고 다시 시작 하는 c + + Interop 기능 때문에 발생할 수 있습니다.

C + + Interop를 사용 하면 일반적으로 사용 되는 COM 구성 요소를 사용 하거나 c + + 클래스 내에서 래핑할 수 있습니다. 이러한 래퍼 클래스를 사용자 지정 런타임 호출 가능 래퍼 또는 CRCWs 라고 하며 응용 프로그램 코드에서 직접 COM을 사용 하는 것 보다 두 가지 이점이 있습니다.

- 결과 클래스는 Visual C++ 이외의 언어로 사용할 수 있습니다.

- COM 인터페이스에 대 한 세부 정보는 관리 되는 클라이언트 코드에서 숨길 수 있습니다. 네이티브 형식 대신 .NET 데이터 형식을 사용할 수 있으며, 데이터 마샬링에 대 한 세부 정보는 CRCW 내에서 투명 하 게 수행할 수 있습니다.

COM이 직접 사용 되는지 아니면 CRCW를 통해 사용 되는지에 관계 없이 단순 blittable 형식 이외의 인수 형식은 마샬링되어야 합니다.

## <a name="blittable-types"></a>Blittable 형식

단순 하 고 내장 형식을 사용 하는 관리 되지 않는 Api의 경우 ( [Blittable 형식 및 비 Blittable 형식](/dotnet/framework/interop/blittable-and-non-blittable-types)참조) 이러한 데이터 형식은 메모리에서 동일 하 게 표시 되지만 좀 더 복잡 한 데이터 형식에는 명시적 데이터 마샬링이 필요 하기 때문에 특수 코딩이 필요 하지 않습니다. 예제는 [방법: PInvoke를 사용 하 여 관리 코드에서 네이티브 Dll 호출](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)을 참조 하세요.

## <a name="example"></a>예제

```cpp
// vcmcppv2_impl_dllimp.cpp
// compile with: /clr:pure user32.lib
using namespace System::Runtime::InteropServices;

// Implicit DLLImport specifying calling convention
extern "C" int __stdcall MessageBeep(int);

// explicit DLLImport needed here to use P/Invoke marshalling because
// System::String ^ is not the type of the first parameter to printf
[DllImport("msvcrt.dll", EntryPoint = "printf", CallingConvention = CallingConvention::Cdecl,  CharSet = CharSet::Ansi)]
// or just
// [DllImport("msvcrt.dll")]
int printf(System::String ^, ...);

int main() {
   // (string literals are System::String by default)
   printf("Begin beep\n");
   MessageBeep(100000);
   printf("Done\n");
}
```

```Output
Begin beep
Done
```

## <a name="in-this-section"></a>섹션 내용

- [방법: c + + Interop를 사용 하 여 ANSI 문자열 마샬링](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [방법: c + + Interop를 사용 하 여 유니코드 문자열 마샬링](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [방법: c + + Interop를 사용 하 여 COM 문자열 마샬링](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

- [방법: c + + Interop를 사용 하 여 구조체 마샬링](../dotnet/how-to-marshal-structures-using-cpp-interop.md)

- [방법: c + + Interop를 사용 하 여 배열 마샬링](../dotnet/how-to-marshal-arrays-using-cpp-interop.md)

- [방법: c + + Interop를 사용 하 여 콜백 및 대리자 마샬링](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)

- [방법: c + + Interop를 사용 하 여 포함 포인터 마샬링](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)

- [방법: System:: String의 문자에 액세스](../dotnet/how-to-access-characters-in-a-system-string.md)

- [방법: char * 문자열을 System:: Byte 배열로 변환](../dotnet/how-to-convert-char-star-string-to-system-byte-array.md)

- [방법: System:: String을 wchar_t * 또는 char로 변환\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)

- [방법: System:: String을 표준 문자열로 변환](../dotnet/how-to-convert-system-string-to-standard-string.md)

- [방법: 표준 문자열을 System:: String으로 변환](../dotnet/how-to-convert-standard-string-to-system-string.md)

- [방법: 바이트 배열에 대 한 포인터 가져오기](../dotnet/how-to-obtain-a-pointer-to-byte-array.md)

- [방법: 관리 되지 않는 리소스를 바이트 배열로 로드](../dotnet/how-to-load-unmanaged-resources-into-a-byte-array.md)

- [방법: 네이티브 함수에서 참조 클래스 수정](../dotnet/how-to-modify-reference-class-in-a-native-function.md)

- [방법: 이미지가 네이티브 인지 CLR 인지 확인](../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)

- [방법: 전역 어셈블리 캐시에 네이티브 DLL 추가](../dotnet/how-to-add-native-dll-to-global-assembly-cache.md)

- [방법: 네이티브 형식에서 값 형식에 대 한 참조 유지](../dotnet/how-to-hold-reference-to-value-type-in-native-type.md)

- [방법: 관리 되지 않는 메모리에 개체 참조 유지](../dotnet/how-to-hold-object-reference-in-unmanaged-memory.md)

- [방법:/clr 컴파일 검색](../dotnet/how-to-detect-clr-compilation.md)

- [방법: System:: Guid와 _GUID 사이에 변환](../dotnet/how-to-convert-between-system-guid-and-guid.md)

- [방법: out 매개 변수 지정](../dotnet/how-to-specify-an-out-parameter.md)

- [방법:/clr 컴파일에서 네이티브 형식 사용](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)

- [방법: 네이티브 형식으로 핸들 선언](../dotnet/how-to-declare-handles-in-native-types.md)

- [방법: C에서 사용 하기 위해 네이티브 클래스 래핑 #](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

Interop 시나리오에서 대리자를 사용 하는 방법에 대 한 자세한 내용은 [delegate (c + + 구성 요소 확장)](../extensions/delegate-cpp-component-extensions.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

- [관리 코드에서 네이티브 함수 호출](../dotnet/calling-native-functions-from-managed-code.md)
