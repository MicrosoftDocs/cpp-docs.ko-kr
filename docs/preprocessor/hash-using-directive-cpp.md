---
title: '#using 지시문(C++/CLI)'
ms.date: 08/29/2019
f1_keywords:
- friend_as_cpp
- '#using'
- friend_as
- '#using_cpp'
helpviewer_keywords:
- using directive (#using)
- '#using directive'
- LIBPATH environment variable
- preprocessor, directives
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
ms.openlocfilehash: 0245eb15219585421be83def0258415ab4b573b6
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684263"
---
# <a name="using-directive-ccli"></a>#using 지시문 (c + +/CLI)

[/Clr](../build/reference/clr-common-language-runtime-compilation.md)을 사용 하 여 컴파일된 프로그램으로 메타 데이터를 가져옵니다.

## <a name="syntax"></a>Syntax

> **`#using`***file* [ **`as_friend`** ]

### <a name="parameters"></a>매개 변수

*파일과*\
MSIL (Microsoft 중간 언어) *`.dll`* , *`.exe`* , *`.netmodule`* 또는 *`.obj`* 파일입니다. 예를 들면 다음과 같습니다.

`#using <MyComponent.dll>`

**`as_friend`**\
*파일* 의 모든 형식에 액세스할 수 있도록 지정 합니다. 자세한 내용은 [Friend 어셈블리 (c + +)](../dotnet/friend-assemblies-cpp.md)를 참조 하세요.

## <a name="remarks"></a>설명

*파일* 은 관리 되는 데이터 및 관리 되는 구문에 대해 가져오는 MSIL (Microsoft 중간 언어) 파일 일 수 있습니다. DLL에 어셈블리 매니페스트가 포함 되어 있으면 매니페스트에서 참조 하는 모든 Dll을 가져옵니다. 빌드 중인 어셈블리는 메타 데이터의 *파일* 을 어셈블리 참조로 나열 합니다.

아마도 *파일* 에 어셈블리가 없고 (*파일* 은 모듈) 현재 (어셈블리) 응용 프로그램의 모듈에서 형식 정보를 사용 하지 않으려는 경우가 있습니다. [/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)를 사용 하 여 모듈이 어셈블리의 일부 임을 나타낼 수 있습니다. 그러면 어셈블리를 참조하는 모든 애플리케이션에서 모듈의 형식을 사용할 수 있습니다.

사용할 수 있는 대안은 **`#using`** [/fu](../build/reference/fu-name-forced-hash-using-file.md) 컴파일러 옵션입니다.

에 전달 된 .exe 어셈블리는 **`#using`** .Net Visual Studio 컴파일러 (예: Visual Basic 또는 Visual c #) 중 하나를 사용 하 여 컴파일해야 합니다.  로 컴파일된 .exe 어셈블리에서 메타 데이터를 가져오려고 **`/clr`** 하면 파일 로드 예외가 발생 합니다.

> [!NOTE]
> 로 참조 되는 구성 요소는 **`#using`** 컴파일 시간에 가져온 다른 버전의 파일을 사용 하 여 실행할 수 있으므로 클라이언트 응용 프로그램에서 예기치 않은 결과가 발생 합니다.

컴파일러가 모듈이 아니라 어셈블리의 형식을 인식할 수 있도록 하려면 해당 형식을 강제로 확인 해야 합니다. 예를 들어 형식의 인스턴스를 정의 하 여 강제로 적용할 수 있습니다. 컴파일러에 대 한 어셈블리의 형식 이름을 확인 하는 다른 방법이 있습니다. 예를 들어 어셈블리의 형식에서 상속 하는 경우 형식 이름이 컴파일러에 알려집니다.

사용 되는 소스 코드에서 빌드된 메타 데이터 [`__declspec(thread)`](../cpp/thread.md) 를 가져올 때 스레드 의미 체계가 메타 데이터에 유지 되지 않습니다. 예를 들어,를 사용 하 여 선언 된 변수는 **`__declspec(thread)`** .NET Framework 공용 언어 런타임으로 빌드된 다음를 통해 가져온 프로그램에서 컴파일되어 **`#using`** **`__declspec(thread)`** 변수에 대 한 의미 체계를 갖지 않습니다.

에서 참조 하는 파일에서 가져온 모든 형식 (관리 및 네이티브) **`#using`** 을 사용할 수 있지만 컴파일러는 네이티브 형식을 정의가 아닌 선언으로 처리 합니다.

mscorlib.dll는를 사용 하 여 컴파일할 때 자동으로 참조 됩니다 **`/clr`** .

LIBPATH 환경 변수는 컴파일러가에 전달 된 파일 이름을 확인 하는 경우 검색할 디렉터리를 지정 합니다 **`#using`** .

컴파일러는 다음 경로를 따라 참조를 검색 합니다.

- 문에 지정 된 경로 **`#using`** 입니다.

- 현재 디렉터리

- .NET Framework 시스템 디렉터리

- 컴파일러 옵션을 사용 하 여 디렉터리를 추가 했습니다 [`/AI`](../build/reference/ai-specify-metadata-directories.md) .

- LIBPATH 환경 변수의 디렉터리

## <a name="examples"></a>예제

다른 어셈블리를 참조 하는 두 번째 어셈블리를 참조 하는 어셈블리를 빌드할 수 있습니다. 해당 형식 중 하나를 명시적으로 사용 하는 경우 첫 번째 어셈블리에서 세 번째 어셈블리를 명시적으로 참조 하기만 하면 됩니다.

```cpp
// using_assembly_A.cpp
// compile with: /clr /LD
public ref class A {};
```

```cpp
// using_assembly_B.cpp
// compile with: /clr /LD
#using "using_assembly_A.dll"
public ref class B {
public:
   void Test(A a) {}
   void Test() {}
};
```

다음 샘플에서는 프로그램에서 *using_assembly_A*에 정의 된 형식을 사용 하지 않기 때문에 *using_assembly_A.dll*참조에 대 한 오류를 보고 하지 않습니다.

```cpp
// using_assembly_C.cpp
// compile with: /clr
#using "using_assembly_B.dll"
int main() {
   B b;
   b.Test();
}
```

## <a name="see-also"></a>추가 정보

[전처리기 지시문](../preprocessor/preprocessor-directives.md)
