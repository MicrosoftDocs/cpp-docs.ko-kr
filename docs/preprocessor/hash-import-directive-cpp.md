---
title: '#import 지시문(C++)'
ms.date: 08/29/2019
f1_keywords:
- '#import'
helpviewer_keywords:
- .tlh files
- '#import directive'
- import directive (#import)
- tlh files
- tlbid switch
- preprocessor, directives
- COM, type library header file
ms.assetid: 787d1112-e543-40d7-ab15-a63d43f4030a
ms.openlocfilehash: 9cdfef091b659151f427c381e386f0e83396e741
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332062"
---
# <a name="import-directive-c"></a>#import 지시문(C++)

**C++ 전용**

형식 라이브러리의 정보를 통합하는 데 사용됩니다. 형식 라이브러리의 콘텐츠는 대부분 COM 인터페이스를 설명하는 C++ 클래스로 변환됩니다.

## <a name="syntax"></a>구문

> **#import** "*파일* \[이름 " *속성*]\
> *파일*> \[이름*특성을* **#import]** \<

### <a name="parameters"></a>매개 변수

*파일*\
가져올 형식 라이브러리를 지정합니다. *파일 이름은* 다음 종류 중 하나일 수 있습니다.

- .olb, .tlb 또는 .dll 파일 등 형식 라이브러리를 포함하는 파일 이름입니다. 키워드 , `file:`"는 각 파일 이름 앞에 수 있습니다.

- 형식 라이브러리에서 제어의 progid입니다. 키워드는 `progid:`각 progid 앞에 옵니다. 다음은 그 예입니다.

    ```cpp
    #import "progid:my.prog.id.1.5"
    ```

   progids에 대한 자세한 내용은 [지역화 ID 및 버전 번호 지정을](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber)참조하십시오.

   64비트 운영 체제에서 32비트 교차 컴파일러를 사용하는 경우 컴파일러는 32비트 레지스트리 하이브만 읽을 수 있습니다. 64비트 형식 라이브러리를 빌드 및 등록하기 위해 네이티브 64비트 컴파일러를 사용할 수도 있습니다.

- 형식 라이브러리의 라이브러리 ID입니다. 키워드는 `libid:`각 라이브러리 ID 앞에 옵니다. 다음은 그 예입니다.

    ```cpp
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")
    ```

   `version` 또는 `lcid`를 지정하지 않은 경우에 적용되는 [규칙](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber)에 `progid:`도 `libid:`에 적용됩니다.

- 실행 파일(.exe)입니다.

- 유형 라이브러리 리소스(예: .ocx)를 포함하는 라이브러리(.dll) 파일입니다.

- 형식 라이브러리를 보유하는 복합 문서입니다.

- **LoadTypeLib** API에서 이해할 수 있는 다른 파일 형식입니다.

*특성*\
하나 이상의 [#import 특성](#_predir_the_23import_directive_import_attributes). 공백이나 쉼표를 사용하여 특성을 구분합니다. 다음은 그 예입니다.

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only
```

\-또는-

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only
```

## <a name="remarks"></a>설명

### <a name="search-order-for-filename"></a><a name="_predir_the_23import_directive_searchorderforfilename"></a>파일 이름 검색 순서

*파일 이름은* 선택적으로 디렉터리 사양 앞에 옵니다. 이 파일 이름은 기존 파일의 이름이어야 합니다. 두 구문 형식의 차이는 경로가 불완전하게 지정되어 있을 경우 전처리기가 형식 라이브러리 파일을 검색하는 순서입니다.

|구문 형식|작업|
|-----------------|------------|
|따옴표로 묶인 형식|전처리기에서 #import 문이 포함된 파일의 디렉토리에서 먼저 형식 라이브러리 파일을 찾은 다음 **해당** 파일을`#include`포함하는 모든 파일의 디렉토리에서 찾아보라고 지시합니다. 그런 다음 전처리기는 아래 표시된 경로를 따라 검색합니다.|
|꺾쇠 괄호 형식|전처리기가 다음 경로에 따라 형식 라이브러리 파일을 검색하도록 지시합니다.<br /><br /> 1. `PATH` 환경 변수 경로 목록<br />2. `LIB` 환경 변수 경로 목록<br />3. 컴파일러가 [no_registry](../preprocessor/no-registry.md) 특성을 가진 다른 형식 라이브러리에서 참조 된 형식 라이브러리를 검색하는 경우를 제외하고 [/I](../build/reference/i-additional-include-directories.md) 컴파일러 옵션에 의해 지정된 경로입니다.|

### <a name="specify-the-localization-id-and-version-number"></a><a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a>지역화 ID 및 버전 번호 지정

progid를 지정할 때 progid의 지역화 ID 및 버전 번호를 지정할 수도 있습니다. 다음은 그 예입니다.

```cpp
#import "progid:my.prog.id" lcid("0") version("4.0)
```

지역화 ID를 지정하지 않으면 다음 규칙에 따라 progid가 선택됩니다.

- 지역화 ID가 하나만 있는 경우 해당 ID가 사용됩니다.

- 지역화 ID가 두 개 이상인 경우 버전 번호 0, 9 또는 409가 있는 첫 번째 지역화 ID가 사용됩니다.

- 둘 이상의 지역화 ID가 있고 그 중 어느 것도 0, 9 또는 409가 아닌 경우 마지막 ID가 사용됩니다.

- 버전 번호를 지정하지 않으면 최신 버전이 사용됩니다.

### <a name="header-files-created-by-import"></a><a name="_predir_the_23import_directive_header_files_created_by_import"></a>가져오기로 만든 헤더 파일

**#import** C++ 소스 코드에서 형식 라이브러리 내용을 재구성하는 두 개의 헤더 파일을 만듭니다. 기본 헤더 파일은 MIDL(Microsoft 인터페이스 정의 언어) 컴파일러에서 생성된 파일과 유사하지만 추가 컴파일러에서 생성된 코드 및 데이터가 있습니다. [기본 헤더 파일에는](#_predir_the_primary_type_library_header_file) 형식 라이브러리와 동일한 기본 이름과 . TLH 확장. 보조 헤더 파일은 .TLI 확장명을 가진 형식 라이브러리와 같은 기본 이름을 가집니다. 이 파일은 컴파일러에서 생성된 멤버 함수에 대한 구현을 포함하고 기본 헤더 파일에 포함(`#include`)되어 있습니다.

매개 변수를 사용하는 `byref` dispinterface 속성을 가져오는 경우 함수에 대한 [__declspec(속성)](../cpp/property-cpp.md) 문을 생성하지 **#import.**

두 헤더 파일은 [/Fo(이름 개체 파일)](../build/reference/fo-object-file-name.md) 옵션으로 지정된 출력 디렉토리에 배치됩니다. 그런 다음 기본 헤더 파일이 `#include` 지시문에 의해 명명된 것처럼 컴파일러에서 읽고 컴파일됩니다.

다음 컴파일러 최적화는 **#import** 지시문과 함께 제공됩니다.

- 헤더 파일은 만들어질 때 형식 라이브러리와 동일한 타임스탬프를 제공받습니다.

- **#import** 처리되면 컴파일러는 헤더가 존재하고 최신 상태인지 먼저 확인합니다. 그렇다면 다시 만들 필요가 없습니다.

**#import** 지시문은 최소 재생성에도 참여하며 미리 컴파일된 헤더 파일에 배치할 수 있습니다.  자세한 내용은 [미리 컴파일된 헤더 파일 만들기를](../build/creating-precompiled-header-files.md)참조하십시오.

### <a name="primary-type-library-header-file"></a><a name="_predir_the_primary_type_library_header_file"></a>기본 형식 라이브러리 헤더 파일

기본 형식 라이브러리 헤더 파일은 다음과 같은 7개의 섹션으로 구성됩니다.

- 제목 상용구: 주석, COMDEF.H용 `#include` 문(헤더에 사용되는 일부 표준 매크로 정의) 및 다른 기타 설정 정보로 구성됩니다.

- 정방향 참조 및 typedef: `struct IMyInterface` 및 typedef와 같은 구조체 선언으로 구성됩니다.

- 스마트 포인터 선언: 템플릿 `_com_ptr_t` 클래스는 스마트 포인터입니다. 인터페이스 포인터를 캡슐화하고 `AddRef`호출 할 필요가 없습니다 . `Release` `QueryInterface` 또한 새 COM `CoCreateInstance` 개체를 만들 때 호출을 숨깁니다. 이 섹션에서는 매크로 `_COM_SMARTPTR_TYPEDEF` 문을 사용하여 COM 인터페이스의 typedefs를 [_com_ptr_t](../cpp/com-ptr-t-class.md) 템플릿 클래스의 템플릿 특수화로 설정합니다. 예를 들어 `IMyInterface`인터페이스의 경우 은 TLH 파일에는 다음이 포함됩니다.

    ```TLH
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
    ```

   컴파일러는 다음과 같이 확장됩니다.

    ```cpp
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;
    ```

   `IMyInterfacePtr` 형식은 원시 인터페이스 포인터 `IMyInterface*` 대신 사용할 수 있습니다. 따라서 다양한 `IUnknown` 멤버 함수를 호출할 필요가 없습니다.

- Typeinfo 선언: 주로 클래스 정의 및 에서 반환 되는 `ITypeLib:GetTypeInfo`개별 typeinfo 항목을 노출 하는 다른 항목으로 구성 됩니다. 이 섹션에서 형식 라이브러리의 각 typeinfo는 `TYPEKIND` 정보에 종속적인 형식의 헤더에 반영됩니다.

- 선택적 기존 형식 GUID 정의: 명명된 GUID 상수의 초기화를 포함합니다. 이러한 이름에는 `CLSID_CoClass` MIDL 컴파일러에서 생성된 이름과 유사한 양식이 `IID_Interface`있습니다.

- 보조 형식 라이브러리 헤더에 대한 `#include` 문입니다.

- 바닥글 상용구: 현재 `#pragma pack(pop)`을 포함합니다.

제목 상용구 및 바닥글 상용구 섹션을 제외한 모든 섹션은 원래 IDL 파일의 `library` 문으로 지정된 이름으로 네임스페이스에 동봉됩니다. 네임스페이스 이름을 사용하는 명시적 자격으로 형식 라이브러리 헤더의 이름을 사용할 수 있습니다. 또는 다음 문을 포함할 수 있습니다.

```cpp
using namespace MyLib;
```

소스 코드에서 **#import** 문 직후에 표시됩니다.

**#import** 지시문 [no_namespace)](no-namespace.md)특성을 사용하여 네임스페이스를 억제할 수 있습니다. 하지만 네임스페이스를 표시하지 않으면 이름이 충돌될 수 있습니다. 네임스페이스는 [rename_namespace](rename-namespace.md) 특성으로 이름을 바꿀 수도 있습니다.

컴파일러는 현재 처리 중인 형식 라이브러리에 필요한 모든 형식 라이브러리 종속성에 대한 전체 경로를 제공합니다. 경로는 컴파일러가 처리된 각 형식 라이브러리에 대해 생성하는 형식 라이브러리 헤더(.TLH)에 주석 형식으로 기록됩니다.

형식 라이브러리에 다른 형식 라이브러리에 정의된 형식에 대한 참조가 포함된 경우 .TLH 파일에 다음과 같은 유형의 주석이 포함됩니다.

```TLH
//
// Cross-referenced type libraries:
//
//  #import "c:\path\typelib0.tlb"
//
```

**#import** 주석의 실제 파일 이름은 레지스트리에 저장된 상호 참조형식 라이브러리의 전체 경로입니다. 형식 정의 누락으로 인해 발생하는 오류가 발생하면 의 머리에서 주석을 확인합니다. TLH를 사용하여 먼저 가져와야 할 종속 형식 라이브러리를 확인합니다. .TLI 파일을 컴파일하는 동안 발생 가능성이 높은 오류는 구문 오류(예: C2143, C2146, C2321), C2501(decl-specifiers 누락) 또는 C2433(데이터 선언에 '인라인'이 허용되지 않음)입니다.

종속성 오류를 해결하려면 시스템 헤더에서 달리 제공하지 않는 종속성 주석을 결정한 다음 종속 형식 라이브러리의 **#import** **지시문** 앞에 #import 지시문을 제공합니다.

### <a name="import-attributes"></a><a name="_predir_the_23import_directive_import_attributes"></a>#import 특성

**#import** 선택적으로 하나 이상의 특성을 포함할 수 있습니다. 이러한 특성은 컴파일러가 형식 라이브러리 헤더의 콘텐츠를 수정하도록 지시합니다. 백슬래시()**\\**기호를 사용하여 단일 **#import** 문에 추가 줄을 포함할 수 있습니다. 다음은 그 예입니다.

```cpp
#import "test.lib" no_namespace \
   rename("OldName", "NewName")
```

자세한 내용은 [#import 특성을](../preprocessor/hash-import-attributes-cpp.md)참조하십시오.

**C++ 전용 종료**

## <a name="see-also"></a>참고 항목

[전처리기 지시문](../preprocessor/preprocessor-directives.md)\
[컴파일러 COM 지원](../cpp/compiler-com-support.md)
