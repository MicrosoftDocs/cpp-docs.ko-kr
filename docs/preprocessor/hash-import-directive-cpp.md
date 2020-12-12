---
description: '자세한 정보: #import 지시문 (c + +)'
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
ms.openlocfilehash: 73768071dd0ee300ad7b2fd2706fda0ed76067ac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269278"
---
# <a name="import-directive-c"></a>#import 지시문 (c + +)

**C++ 전용**

형식 라이브러리의 정보를 통합하는 데 사용됩니다. 형식 라이브러리의 콘텐츠는 대부분 COM 인터페이스를 설명하는 C++ 클래스로 변환됩니다.

## <a name="syntax"></a>Syntax

> **#import** "*filename*" \[ *특성*] \
> **#import** \<*filename*> \[ *특성*]

### <a name="parameters"></a>매개 변수

*이름도*\
가져올 형식 라이브러리를 지정합니다. *파일 이름은* 다음 중 하나일 수 있습니다.

- .olb, .tlb 또는 .dll 파일 등 형식 라이브러리를 포함하는 파일 이름입니다. 키워드는 `file:` 각 파일 이름 앞에 올 수 있습니다.

- 형식 라이브러리에서 제어의 progid입니다. 키워드는 `progid:` 각 progid 앞에 올 수 있습니다. 예를 들어:

    ```cpp
    #import "progid:my.prog.id.1.5"
    ```

   Progid에 대 한 자세한 내용은 [지역화 ID 및 버전 번호 지정](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber)을 참조 하세요.

   64 비트 운영 체제에서 32 비트 크로스 컴파일러를 사용 하는 경우 컴파일러는 32 비트 레지스트리 hive만 읽을 수 있습니다. 64비트 형식 라이브러리를 빌드 및 등록하기 위해 네이티브 64비트 컴파일러를 사용할 수도 있습니다.

- 형식 라이브러리의 라이브러리 ID입니다. 키워드는 `libid:` 각 라이브러리 ID 앞에 올 수 있습니다. 예를 들어:

    ```cpp
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")
    ```

   `version` 또는 `lcid`를 지정하지 않은 경우에 적용되는 [규칙](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber)에 `progid:`도 `libid:`에 적용됩니다.

- 실행 파일(.exe)입니다.

- 형식 라이브러리 리소스 (예: .ocx)를 포함 하는 라이브러리 파일 (.dll)입니다.

- 형식 라이브러리를 보유하는 복합 문서입니다.

- **Loadtypelib** API가 인식할 수 있는 다른 모든 파일 형식입니다.

*특성*\
하나 이상의 [#import 특성](#_predir_the_23import_directive_import_attributes)입니다. 공백이나 쉼표를 사용하여 특성을 구분합니다. 예를 들어:

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only
```

\-또는-

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only
```

## <a name="remarks"></a>설명

### <a name="search-order-for-filename"></a><a name="_predir_the_23import_directive_searchorderforfilename"></a> 파일 이름에 대 한 검색 순서

*filename* 은 선택적으로 디렉터리 사양 뒤에 옵니다. 이 파일 이름은 기존 파일의 이름이어야 합니다. 두 구문 형식의 차이는 경로가 불완전하게 지정되어 있을 경우 전처리기가 형식 라이브러리 파일을 검색하는 순서입니다.

|구문 형식|작업|
|-----------------|------------|
|따옴표로 묶인 형식|전처리기는 **#import** 문을 포함 하는 파일의 디렉터리에서 먼저 형식 라이브러리 파일을 검색 한 다음 해당 파일을 포함 하는 파일 ()의 디렉터리에서 형식 라이브러리 파일을 찾도록 지시 합니다 `#include` . 그런 다음 전처리기는 아래 표시된 경로를 따라 검색합니다.|
|꺾쇠 괄호 형식|전처리기가 다음 경로에 따라 형식 라이브러리 파일을 검색하도록 지시합니다.<br /><br /> 1. `PATH` 환경 변수 경로 목록<br />2. `LIB` 환경 변수 경로 목록<br />3. [no_registry](../preprocessor/no-registry.md) 특성을 사용 하 여 다른 형식 라이브러리에서 참조 된 형식 라이브러리를 컴파일러가 검색 한다는 점을 제외 하 고 [/i](../build/reference/i-additional-include-directories.md) 컴파일러 옵션으로 지정 된 경로입니다.|

### <a name="specify-the-localization-id-and-version-number"></a><a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a> 지역화 ID 및 버전 번호를 지정 합니다.

progid를 지정할 때 progid의 지역화 ID 및 버전 번호를 지정할 수도 있습니다. 예를 들어:

```cpp
#import "progid:my.prog.id" lcid("0") version("4.0)
```

지역화 ID를 지정 하지 않는 경우 progid는 다음 규칙에 따라 선택 됩니다.

- 지역화 ID가 하나만 있는 경우 해당 ID가 사용 됩니다.

- 둘 이상의 지역화 ID가 있는 경우 버전 번호가 0, 9 또는 409 인 첫 번째 ID가 사용 됩니다.

- 둘 이상의 지역화 ID가 있으며 0, 9 또는 409이 아닌 경우 마지막 항목이 사용 됩니다.

- 버전 번호를 지정 하지 않으면 최신 버전이 사용 됩니다.

### <a name="header-files-created-by-import"></a><a name="_predir_the_23import_directive_header_files_created_by_import"></a> 가져오기로 만든 헤더 파일

**#import** c + + 소스 코드에서 형식 라이브러리 콘텐츠를 다시 생성 하는 두 개의 헤더 파일을 만듭니다. 주 헤더 파일은 Microsoft 인터페이스 정의 언어 (MIDL) 컴파일러에서 생성 된 것과 유사 하지만 컴파일러에서 생성 된 추가 코드와 데이터를 포함 합니다. [기본 헤더 파일](#_predir_the_primary_type_library_header_file) 은 형식 라이브러리와 같은 기본 이름을 포함 합니다. .TLH 확장입니다. 보조 헤더 파일은 .TLI 확장명을 가진 형식 라이브러리와 같은 기본 이름을 가집니다. 이 파일은 컴파일러에서 생성된 멤버 함수에 대한 구현을 포함하고 기본 헤더 파일에 포함(`#include`)되어 있습니다.

매개 변수를 사용 하는 트 속성을 가져오는 경우 `byref` **#import** 는 함수에 대 한 [__declspec (속성)](../cpp/property-cpp.md) 문을 생성 하지 않습니다.

두 헤더 파일은 모두 [/fo (이름 개체 파일)](../build/reference/fo-object-file-name.md) 옵션으로 지정 된 출력 디렉터리에 배치 됩니다. 그런 다음 지시문에 의해 기본 헤더 파일의 이름을 지정 하는 것 처럼 컴파일러에서이를 읽고 컴파일합니다 `#include` .

다음 컴파일러 최적화는 **#import** 지시문과 함께 제공 됩니다.

- 헤더 파일은 만들어질 때 형식 라이브러리와 동일한 타임스탬프를 제공받습니다.

- **#Import** 처리 될 때 컴파일러는 먼저 헤더가 존재 하 고 최신 상태 인지 확인 합니다. 그렇다면 다시 만들 필요가 없습니다.

또한 **#import** 지시어는 최소 다시 빌드에 참여 하 고 미리 컴파일된 헤더 파일에 배치할 수 있습니다.  자세한 내용은 [미리 컴파일된 헤더 파일 만들기](../build/creating-precompiled-header-files.md)를 참조 하세요.

### <a name="primary-type-library-header-file"></a><a name="_predir_the_primary_type_library_header_file"></a> 기본 형식 라이브러리 헤더 파일

기본 형식 라이브러리 헤더 파일은 다음과 같은 7개의 섹션으로 구성됩니다.

- 제목 상용구: 주석, COMDEF.H용 `#include` 문(헤더에 사용되는 일부 표준 매크로 정의) 및 다른 기타 설정 정보로 구성됩니다.

- 정방향 참조 및 typedef: `struct IMyInterface` 및 typedef와 같은 구조체 선언으로 구성됩니다.

- 스마트 포인터 선언: 템플릿 클래스는 `_com_ptr_t` 스마트 포인터입니다. 인터페이스 포인터를 캡슐화 하 고, 및 함수를 호출 하지 않아도 `AddRef` `Release` `QueryInterface` 됩니다. 또한 `CoCreateInstance` 새 COM 개체를 만들 때 호출을 숨깁니다. 이 섹션에서는 매크로 문을 사용 하 여 `_COM_SMARTPTR_TYPEDEF` [_com_ptr_t](../cpp/com-ptr-t-class.md) 템플릿 클래스의 템플릿 특수화로 COM 인터페이스의 형식 정의를 설정 합니다. 예를 들어 인터페이스의 경우 `IMyInterface` 입니다. .TLH 파일에는 다음이 포함 됩니다.

    ```TLH
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
    ```

   컴파일러는 다음과 같이 확장됩니다.

    ```cpp
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;
    ```

   `IMyInterfacePtr` 형식은 원시 인터페이스 포인터 `IMyInterface*` 대신 사용할 수 있습니다. 따라서 다양 한 멤버 함수를 호출할 필요가 없습니다. `IUnknown`

- Typeinfo 선언: 주로 클래스 정의와에서 반환 되는 개별 typeinfo 항목을 표시 하는 기타 항목으로 구성 됩니다 `ITypeLib:GetTypeInfo` . 이 섹션에서 형식 라이브러리의 각 typeinfo는 `TYPEKIND` 정보에 종속적인 형식의 헤더에 반영됩니다.

- 선택적 기존 형식 GUID 정의: 명명된 GUID 상수의 초기화를 포함합니다. 이러한 이름의 형식은 `CLSID_CoClass` `IID_Interface` MIDL 컴파일러에 의해 생성 된 이름과 비슷합니다.

- 보조 형식 라이브러리 헤더에 대한 `#include` 문입니다.

- 바닥글 상용구: 현재 `#pragma pack(pop)`을 포함합니다.

상용구 및 바닥글 상용구 섹션을 제외한 모든 섹션은 `library` 원본 IDL 파일의 문에 지정 된 이름과 함께 네임 스페이스에 포함 됩니다. 네임 스페이스 이름을 사용 하 여 명시적 한정으로 형식 라이브러리 헤더의 이름을 사용할 수 있습니다. 또는 다음 문을 포함할 수 있습니다.

```cpp
using namespace MyLib;
```

소스 코드의 **#import** 문 바로 뒤에 있습니다.

**#Import** 지시문의 [no_namespace](no-namespace.md)) 특성을 사용 하 여 네임 스페이스를 억제할 수 있습니다. 하지만 네임스페이스를 표시하지 않으면 이름이 충돌될 수 있습니다. [Rename_namespace](rename-namespace.md) 특성을 통해 네임 스페이스의 이름을 바꿀 수도 있습니다.

컴파일러는 현재 처리 하 고 있는 형식 라이브러리에 필요한 모든 형식 라이브러리 종속성에 대 한 전체 경로를 제공 합니다. 경로는 컴파일러가 처리된 각 형식 라이브러리에 대해 생성하는 형식 라이브러리 헤더(.TLH)에 주석 형식으로 기록됩니다.

형식 라이브러리에 다른 형식 라이브러리에 정의된 형식에 대한 참조가 포함된 경우 .TLH 파일에 다음과 같은 유형의 주석이 포함됩니다.

```TLH
//
// Cross-referenced type libraries:
//
//  #import "c:\path\typelib0.tlb"
//
```

**#Import** 주석의 실제 파일 이름은 레지스트리에 저장 된 대로 상호 참조 된 형식 라이브러리의 전체 경로입니다. 형식 정의 누락으로 인해 발생 하는 오류가 발생 하는 경우에는의 맨 위에 있는 주석을 확인 하십시오. .TLH는 먼저 가져올 종속 형식 라이브러리를 확인 합니다. .TLI 파일을 컴파일하는 동안 발생 가능성이 높은 오류는 구문 오류(예: C2143, C2146, C2321), C2501(decl-specifiers 누락) 또는 C2433(데이터 선언에 '인라인'이 허용되지 않음)입니다.

종속성 오류를 해결 하려면 시스템 헤더에서 다른 방법으로 제공 되지 않는 종속성 주석을 확인 한 다음 종속 형식 라이브러리의 **#import** 지시문 앞의 특정 지점에 **#import** 지시어를 제공 합니다.

### <a name="import-attributes"></a><a name="_predir_the_23import_directive_import_attributes"></a> #import 특성

**#import** 은 하나 이상의 특성을 선택적으로 포함할 수 있습니다. 이러한 특성은 컴파일러가 형식 라이브러리 헤더의 콘텐츠를 수정하도록 지시합니다. 백슬래시 ( **\\** ) 기호를 사용 하 여 단일 **#import** 문에 추가 줄을 포함할 수 있습니다. 예를 들어:

```cpp
#import "test.lib" no_namespace \
   rename("OldName", "NewName")
```

자세한 내용은 [#import 특성](../preprocessor/hash-import-attributes-cpp.md)을 참조 하세요.

**C++ 전용 종료**

## <a name="see-also"></a>참고 항목

[전처리기 지시문](../preprocessor/preprocessor-directives.md)\
[컴파일러 COM 지원](../cpp/compiler-com-support.md)
