---
title: '#특성 (c + +) 가져오기 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- '#import directive, attributes'
ms.assetid: 2a5085e3-82ee-4f83-892b-0aa6cc13863b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d1e69f977ffaacdfd2bb8bb0f53d3fe197af3fad
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842290"
---
# <a name="import-attributes-c"></a>#import 특성 (C++)
#import 지시문에 사용된 특성에 대한 링크를 제공합니다.  
  
 **Microsoft 전용**  
  
 다음 특성은 #import 지시문에서 사용할 수 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|[auto_rename](../preprocessor/auto-rename.md)|변수 이름에 잠재적인 이름 충돌을 해결하는 두 개의 밑줄(__)을 추가하여 C++ 예약어의 이름을 바꿉니다.|  
|[auto_search](../preprocessor/auto-search.md)|형식 라이브러리를 #import로 참조하고 형식 라이브러리 자체가 다른 형식 라이브러리를 참조할 때 컴파일러가 다른 형식 라이브러리에 대해 암시적 #import를 수행할 수 있도록 지정합니다.|  
|[embedded_idl](../preprocessor/embedded-idl.md)|특성에서 생성된 코드를 유지한 상태에서 형식 라이브러리가 .tlh 파일에 작성되도록 지정합니다.|  
|[exclude](../preprocessor/exclude-hash-import.md)|생성되는 형식 라이브러리 헤더 파일에서 항목을 제외시킵니다.|  
|[high_method_prefix](../preprocessor/high-method-prefix.md)|상위 수준 속성과 메서드 명명에 사용될 접두사를 지정합니다.|  
|[high_property_prefixes](../preprocessor/high-property-prefixes.md)|세 가지 속성 메서드의 대체 접두사를 지정합니다.|  
|[implementation_only](../preprocessor/implementation-only.md)|.tlh 헤더 파일(기본 헤더 파일)을 생성하지 않습니다.|  
|[include()](../preprocessor/include-parens.md)|자동 제외를 사용하지 않도록 설정합니다.|  
|[inject_statement](../preprocessor/inject-statement.md)|소스 텍스트로서 인수를 형식 라이브러리 헤더에 삽입합니다.|  
|[named_guids](../preprocessor/named-guids.md)|정의 하 고 폼의 이전 스타일의 GUID 변수를 초기화 하는 컴파일러가 **LIBID_MyLib**, **CLSID_MyCoClass**, **IID_MyInterface**, 및 **DIID _MyDispInterface**합니다.|  
|[no_auto_exclude](../preprocessor/no-auto-exclude.md)|자동 제외를 사용하지 않도록 설정합니다.|  
|[no_dual_interfaces](../preprocessor/no-dual-interfaces.md)|컴파일러가 이중 인터페이스 메서드에 대한 래퍼 함수를 생성하는 방법을 변경합니다.|  
|[no_implementation](../preprocessor/no-implementation.md)|래퍼 멤버 함수의 구현이 포함된 .tli 헤더를 생성하지 않습니다.|  
|[no_namespace](../preprocessor/no-namespace.md)|컴파일러가 생성하지 않은 네임스페이스 이름을 지정합니다.|  
|[no_registry](../preprocessor/no-registry.md)|형식 라이브러리에 대한 레지스트리를 검색하지 않도록 컴파일러에 지시합니다.|  
|[no_search_namespace](../preprocessor/no-search-namespace.md)|와 동일한 기능에는 [no_namespace](../preprocessor/no-namespace.md) 특성 하지만 #import 지시어를 함께 사용 하는 형식 라이브러리에 사용 되는 [auto_search](../preprocessor/auto-search.md) 특성입니다.|  
|[no_smart_pointers](../preprocessor/no-smart-pointers.md)|형식 라이브러리의 모든 인터페이스에 대한 스마트 포인터를 만들지 않습니다.|  
|[raw_dispinterfaces](../preprocessor/raw-dispinterfaces.md)|호출 하는 dispinterface 메서드 및 속성에 대 한 하위 수준의 래퍼 함수를 생성 하는 컴파일러가 **idispatch:: Invoke** 다음 다시 돌아와 `HRESULT` 오류 코드입니다.|  
|[raw_interfaces_only](../preprocessor/raw-interfaces-only.md)|오류 처리 래퍼 함수를 생성 하지 않습니다 및 [속성](../cpp/property-cpp.md) 이러한 래퍼 함수를 사용 하는 선언 합니다.|  
|[raw_method_prefix](../preprocessor/raw-method-prefix.md)|이름 충돌을 방지하기 위해 다른 접두사를 지정합니다.|  
|[raw_native_types](../preprocessor/raw-native-types.md)|상위 수준의 래퍼 함수에서 COM 지원 클래스를 사용하지 않도록 설정하고 대신 하위 수준의 데이터 형식을 사용하도록 합니다.|  
|[raw_property_prefixes](../preprocessor/raw-property-prefixes.md)|세 가지 속성 메서드의 대체 접두사를 지정합니다.|  
|[rename](../preprocessor/rename-hash-import.md)|이름 충돌 문제 해결 작업|  
|[rename_namespace](../preprocessor/rename-namespace.md)|형식 라이브러리의 콘텐츠가 들어있는 네임스페이스의 이름을 바꿉니다.|  
|[rename_search_namespace](../preprocessor/rename-search-namespace.md)|와 동일한 기능에는 [rename_namespace](../preprocessor/rename-namespace.md) 특성 하지만 #import 지시어를 함께 사용 하는 형식 라이브러리에 사용 되는 [auto_search](../preprocessor/auto-search.md) 특성입니다.|  
|[tlbid](../preprocessor/tlbid.md)|기본 형식 라이브러리 이외의 라이브러리를 로드할 수 있도록 합니다.|  
  
 **Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [#import 지시문](../preprocessor/hash-import-directive-cpp.md)