---
description: Stand-Alone 특성에 대해 자세히 알아보세요.
title: Stand-Alone 특성 (c + + COM)
ms.date: 10/02/2018
helpviewer_keywords:
- standalone attributes
- attributes [C++/CLI], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
ms.openlocfilehash: 39b7356243f9b6ba7c42e907ca0733f59b85961e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329596"
---
# <a name="stand-alone-attributes"></a>독립 실행형 특성

독립형 특성은 c + + 키워드에서 작동 하지 않지만 코드 줄과 유사 합니다. 독립형 특성 문에는 줄 끝에 세미콜론이 필요 합니다.

## <a name="stand-alone-attribute-list"></a>독립형 특성 목록

|특성|설명|
|---------------|-----------------|
|[cpp_quote](cpp-quote.md)|지정 된 문자열을 인용 문자 없이 생성 된 헤더 파일에 내보냅니다.|
|[재구성](custom-cpp.md)|사용자 고유의 특성을 정의할 수 있습니다.|
|[db_command](db-command.md)|OLE DB 명령을 만듭니다.|
|[emitidl](emitidl.md)|모든 후속 IDL 특성을 처리 하 여 생성 된 .idl 파일에 배치할지 여부를 결정 합니다.|
|[idl_module](idl-module.md)|DLL의 진입점을 지정 합니다.|
|[idl_quote](idl-quote.md)|Visual C++ 현재 버전에서 지원 되지 않는 IDL 구문을 사용 하 여 생성 된 .idl 파일로 전달할 수 있습니다.|
|[import](import.md)|기본 .idl 파일에서 참조 하려는 정의를 포함 하는 다른 .idl, odl 또는 .h 파일을 지정 합니다.|
|[importidl](importidl.md)|지정 된 .idl 파일을 생성 된 .idl 파일에 삽입 합니다.|
|[importlib](importlib.md)|다른 형식 라이브러리에 이미 컴파일된 형식을 만들고 있는 형식 라이브러리에서 사용할 수 있도록 합니다.|
|[되어야](include-cpp.md)|생성 된 .idl 파일에 포함할 하나 이상의 헤더 파일을 지정 합니다.|
|[includelib](includelib-cpp.md)|.Idl 또는 .h 파일을 생성 된 .idl 파일에 포함 시킵니다.|
|[library_block](library-block.md)|.Idl 파일의 라이브러리 블록 안에 구문을 배치 합니다.|
|[모듈](module-cpp.md)|.Idl 파일의 라이브러리 블록을 정의합니다.|
|[no_injected_text](no-injected-text.md)|컴파일러가 특성 사용의 결과로 코드를 삽입 하지 않도록 합니다.|
|[pragma](pragma.md)|지정 된 문자열을 인용 문자 없이 생성 된 .idl 파일로 내보냅니다.|

## <a name="see-also"></a>참고 항목

[사용 별 특성](attributes-by-usage.md)
