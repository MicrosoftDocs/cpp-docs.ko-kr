---
description: '다음에 대 한 자세한 정보: #import 특성 (c + +)'
title: '#import 특성(C++)'
ms.date: 08/29/2019
helpviewer_keywords:
- '#import directive, attributes'
ms.assetid: 2a5085e3-82ee-4f83-892b-0aa6cc13863b
ms.openlocfilehash: 87719ba549efab4e0acf13d7e957c6841900d5fc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300454"
---
# <a name="import-attributes-c"></a>#import 특성 (c + +)

지시문에 사용 되는 특성에 대 한 링크를 제공 `#import` 합니다.

**Microsoft 전용**

지시문에 사용할 수 있는 특성은 다음과 같습니다 `#import` .

|특성|설명|
|---------------|-----------------|
|[auto_rename](../preprocessor/auto-rename.md)|변수 이름에 잠재적인 이름 충돌을 해결하는 두 개의 밑줄(__)을 추가하여 C++ 예약어의 이름을 바꿉니다.|
|[auto_search](../preprocessor/auto-search.md)|형식 라이브러리를 #import로 참조하고 형식 라이브러리 자체가 다른 형식 라이브러리를 참조할 때 컴파일러가 다른 형식 라이브러리에 대해 암시적 #import를 수행할 수 있도록 지정합니다.|
|[embedded_idl](../preprocessor/embedded-idl.md)|특성에서 생성된 코드를 유지한 상태에서 형식 라이브러리가 .tlh 파일에 작성되도록 지정합니다.|
|[시키고](../preprocessor/exclude-hash-import.md)|생성되는 형식 라이브러리 헤더 파일에서 항목을 제외시킵니다.|
|[high_method_prefix](../preprocessor/high-method-prefix.md)|상위 수준 속성과 메서드 명명에 사용될 접두사를 지정합니다.|
|[high_property_prefixes](../preprocessor/high-property-prefixes.md)|세 가지 속성 메서드의 대체 접두사를 지정합니다.|
|[implementation_only](../preprocessor/implementation-only.md)|.tlh 헤더 파일(기본 헤더 파일)을 생성하지 않습니다.|
|[include ()](../preprocessor/include-parens.md)|자동 제외를 사용하지 않도록 설정합니다.|
|[inject_statement](../preprocessor/inject-statement.md)|소스 텍스트로서 인수를 형식 라이브러리 헤더에 삽입합니다.|
|[named_guids](../preprocessor/named-guids.md)|는,, 및 형식의 GUID 변수를 이전 스타일로 정의 하 고 초기화 하도록 컴파일러에 지시 `LIBID_MyLib` `CLSID_MyCoClass` `IID_MyInterface` `DIID_MyDispInterface` 합니다.|
|[no_auto_exclude](../preprocessor/no-auto-exclude.md)|자동 제외를 사용하지 않도록 설정합니다.|
|[no_dual_interfaces](../preprocessor/no-dual-interfaces.md)|컴파일러가 이중 인터페이스 메서드에 대한 래퍼 함수를 생성하는 방법을 변경합니다.|
|[no_implementation](../preprocessor/no-implementation.md)|래퍼 멤버 함수의 구현이 포함된 .tli 헤더를 생성하지 않습니다.|
|[no_namespace](../preprocessor/no-namespace.md)|컴파일러가 생성하지 않은 네임스페이스 이름을 지정합니다.|
|[no_registry](../preprocessor/no-registry.md)|형식 라이브러리에 대한 레지스트리를 검색하지 않도록 컴파일러에 지시합니다.|
|[no_search_namespace](../preprocessor/no-search-namespace.md)|에는 [no_namespace](../preprocessor/no-namespace.md) 특성과 동일한 기능이 있지만 #import 지시문을 [auto_search](../preprocessor/auto-search.md) 특성과 함께 사용 하는 형식 라이브러리에 사용 됩니다.|
|[no_smart_pointers](../preprocessor/no-smart-pointers.md)|형식 라이브러리의 모든 인터페이스에 대한 스마트 포인터를 만들지 않습니다.|
|[raw_dispinterfaces](../preprocessor/raw-dispinterfaces.md)|을 호출 하 고 HRESULT 오류 코드를 반환 하는 속성 및 속성에 대 한 하위 수준 래퍼 함수를 생성 하도록 컴파일러에 지시 `IDispatch::Invoke` 합니다.|
|[raw_interfaces_only](../preprocessor/raw-interfaces-only.md)|이러한 래퍼 함수를 사용 하는 오류 처리 래퍼 함수 및 [속성](../cpp/property-cpp.md) 선언 생성을 억제 합니다.|
|[raw_method_prefix](../preprocessor/raw-method-prefix.md)|이름 충돌을 방지하기 위해 다른 접두사를 지정합니다.|
|[원시 네이티브 형식](../preprocessor/raw-native-types.md)|상위 수준의 래퍼 함수에서 COM 지원 클래스를 사용하지 않도록 설정하고 대신 하위 수준의 데이터 형식을 사용하도록 합니다.|
|[raw_property_prefixes](../preprocessor/raw-property-prefixes.md)|세 가지 속성 메서드의 대체 접두사를 지정합니다.|
|[rename](../preprocessor/rename-hash-import.md)|이름 충돌 문제 해결 작업|
|[네임스페이스 이름 변경](../preprocessor/rename-namespace.md)|형식 라이브러리의 콘텐츠가 들어있는 네임스페이스의 이름을 바꿉니다.|
|[rename_search_namespace](../preprocessor/rename-search-namespace.md)|에는 [rename_namespace](../preprocessor/rename-namespace.md) 특성과 동일한 기능이 있지만 #import 지시문을 [auto_search](../preprocessor/auto-search.md) 특성과 함께 사용 하는 형식 라이브러리에 사용 됩니다.|
|[tlbid](../preprocessor/tlbid.md)|기본 형식 라이브러리 이외의 라이브러리를 로드할 수 있도록 합니다.|

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[#import 지시문](../preprocessor/hash-import-directive-cpp.md)
