---
description: '자세히 알아보기: module (c + +)'
title: module (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.module
helpviewer_keywords:
- module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
ms.openlocfilehash: 1780ebcb89e7d19f3f3a4c2656d383725d85657a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327482"
---
# <a name="module-c"></a>module(C++)

.Idl 파일의 라이브러리 블록을 정의합니다.

## <a name="syntax"></a>구문

```cpp
[ module (type=dll, name=string, version=1.0, uuid=uuid, lcid=integer, control=boolean, helpstring=string, helpstringdll=string, helpfile=string, helpcontext=integer, helpstringcontext=integer, hidden=boolean, restricted=boolean, custom=string, resource_name=string,) ];
```

### <a name="parameters"></a>매개 변수

*type*<br/>
필드 다음 중 하나일 수 있습니다.

- `dll` 결과 DLL이 in-process COM 서버로 작동 하도록 허용 하는 함수 및 클래스를 추가 합니다. 기본값입니다.

- `exe` 결과 실행 파일이 out-of-process COM 서버로 작동 하도록 허용 하는 함수 및 클래스를 추가 합니다.

- `service` 결과 실행 파일이 NT 서비스로 작동 하도록 허용 하는 함수 및 클래스를 추가 합니다.

- `unspecified` 모듈 특성과 관련 된 ATL 코드의 삽입을 사용 하지 않도록 설정 합니다. ATL 모듈 클래스, 전역 인스턴스 _AtlModule 및 진입점 함수의 삽입입니다. 프로젝트의 기타 특성으로 인한 ATL 코드의 삽입은 허용합니다.

*name*<br/>
필드 라이브러리 블록의 이름입니다.

*version*<br/>
필드 라이브러리 블록에 할당 하려는 버전 번호입니다. 기본값은 1.0입니다.

*uuid*<br/>
라이브러리에 대한 고유 ID입니다. 이 매개 변수를 생략하면 라이브러리에 대한 ID가 자동으로 생성됩니다. 라이브러리 블록의 *uuid* 를 검색해야 할 수 있습니다. **__uuidof(** *libraryname* **)** 식별자를 사용하여 수행할 수 있습니다.

*lcid*<br/>
지역화 매개 변수입니다. 자세한 내용은 [lcid](/windows/win32/Midl/lcid) 를 참조하세요.

*control*<br/>
필드 라이브러리의 모든 coclass가 컨트롤 임을 지정 합니다.

*helpstring*<br/>
형식 라이브러리를 지정합니다.

*typelib*<br/>
필드 문서 문자열 조회를 수행 하는 데 사용할 .dll 파일의 이름을 설정 합니다. 자세한 내용은 [helpstringdll](/windows/win32/Midl/helpstringdll) 을 참조하세요.

*helpfile*<br/>
필드 형식 라이브러리에 대 한 **도움말** 파일의 이름입니다.

*helpcontext*<br/>
필드 이 형식 라이브러리에 대 한 **도움말 ID** 입니다.

*helpstringcontext*<br/>
필드 자세한 내용은 [helpstringcontext](helpstringcontext.md) 를 참조 하세요.

*은선제거*<br/>
필드 전체 라이브러리가 표시 되지 않도록 합니다. 이 사용법은 컨트롤과 함께 사용하기 위한 것입니다. 호스트는 확장된 속성을 사용하여 컨트롤을 래핑하는 새로운 형식 라이브러리를 만들어야 합니다. 자세한 내용은 [hidden](/windows/win32/Midl/hidden) MIDL 특성을 참조하세요.

*액세스가*<br/>
필드 라이브러리의 멤버를 임의로 호출할 수 없습니다. 자세한 내용은 [restricted](/windows/win32/Midl/restricted) MIDL 특성을 참조하세요.

*재구성*<br/>
필드 하나 이상의 특성 이는 [사용자 지정](custom-cpp.md) 특성과 유사 합니다. *사용자 지정* 의 첫 번째 매개 변수는 특성의 GUID입니다. 예를 들어:

```
[module(custom={guid,1}, custom={guid1,2})]
```

*resource_name*<br/>
DLL, 실행 파일 또는 서비스의 APP ID를 등록하는 데 사용되는 .rgs 파일의 문자열 리소스 ID입니다. 모듈이 형식 서비스인 경우 서비스 이름을 포함하는 문자열의 ID를 가져오는 데에도 이 인수가 사용됩니다.

> [!NOTE]
> 서비스 이름을 포함하는 문자열과 .rgs 파일 모두 동일한 숫자 값을 포함해야 합니다.

## <a name="remarks"></a>설명

*restricted* 매개 변수를 [emitidl](emitidl.md)로 지정하지 않는 경우, C++ 특성을 사용하는 프로그램에 **module** 이 필요합니다.

소스 코드가 **module** 특성 외에 [dispinterface](dispinterface.md), [dual](dual.md), [object](object-cpp.md)특성 또는 [coclass](coclass.md)를 암시하는 특성을 사용하는 경우 라이브러리 블록이 만들어집니다.

.idl 파일 하나에 라이브러리 블록 하나가 허용됩니다. 소스 코드에 여러 모듈 항목이 병합되며, 가장 최근의 매개 변수 값이 구현됩니다.

ATL을 사용하는 프로젝트 내에서 이 특성을 사용하는 경우 특성의 동작이 변경됩니다. 특성은 위의 동작 외에도 `_AtlModule` 올바른 형식 및 추가 지원 코드의 전역 개체 (이라고 함)를 삽입 합니다. 독립 실행형 특성의 경우 올바른 모듈 형식에서 파생된 클래스를 삽입합니다. 클래스에 적용되는 특성의 경우 올바른 모듈 형식의 기본 클래스를 추가합니다. 올바른 형식은 *형식* 매개 변수 값에 의해 결정 됩니다.

- `type` = **gdiplus.dll**

   [CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md) 는 COM 서버에 필요한 기본 클래스 및 표준 DLL 진입점으로 사용됩니다. 이러한 진입점은 [DllMain](/windows/win32/Dlls/dllmain), [DllRegisterServer](/windows/win32/api/olectl/nf-olectl-dllregisterserver), [DllUnRegisterServer](/windows/win32/api/olectl/nf-olectl-dllunregisterserver), [DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)및 [DllGetClassObject](/windows/win32/api/combaseapi/nf-combaseapi-dllgetclassobject)입니다.

- `type` = **convert.exe**

   [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) 는 기본 클래스 및 표준 실행 파일 진입점 [WinMain](/windows/win32/api/winbase/nf-winbase-winmain)으로 사용됩니다.

- `type` = **출력소**

   [CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) 는 기본 클래스 및 표준 실행 파일 진입점 [WinMain](/windows/win32/api/winbase/nf-winbase-winmain)으로 사용됩니다.

- `type` = **지정 되지 않은**

   모듈 특성과 관련된 ATL 코드의 삽입이 사용되지 않습니다.

## <a name="example"></a>예제

다음 코드는 생성된 .idl 파일의 라이브러리 블록을 만드는 방법을 보여 줍니다.

```cpp
// cpp_attr_ref_module1.cpp
// compile with: /LD
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];
```

다음 코드는 **module** 사용 결과 삽입된 코드에 나타날 수 있는 함수의 자체 구현을 제공할 수 있음을 보여 줍니다. 삽입된 코드 보기에 대한 자세한 정보는 [/Fx](../../build/reference/fx-merge-injected-code.md) 를 참조하세요. **module** 특성에 의해 삽입된 함수 중 하나를 재정의하려면 함수의 구현을 포함할 클래스를 만들고 여기에 **module** 특성을 적용합니다.

```cpp
// cpp_attr_ref_module2.cpp
// compile with: /LD /link /OPT:NOREF
#include <atlbase.h>
#include <atlcom.h>
#include <atlwin.h>
#include <atltypes.h>
#include <atlctl.h>
#include <atlhost.h>
#include <atlplus.h>

// no semicolon after attribute block
[module(dll, name="MyLibrary", version="1.2", helpfile="MyHelpFile")]
// module attribute now applies to this class
class CMyClass {
public:
BOOL WINAPI DllMain(DWORD dwReason, LPVOID lpReserved) {
   // add your own code here
   return __super::DllMain(dwReason, lpReserved);
   }
};
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|원하는 위치|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[클래스 특성](class-attributes.md)<br/>
[독립형 특성](stand-alone-attributes.md)<br/>
[Typedef, Enum, Union 및 Struct 특성](typedef-enum-union-and-struct-attributes.md)<br/>
[usesgetlasterror](usesgetlasterror.md)<br/>
[라이브러리](/windows/win32/Midl/library)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)<br/>
[helpfile](helpfile.md)<br/>
[version](version-cpp.md)
