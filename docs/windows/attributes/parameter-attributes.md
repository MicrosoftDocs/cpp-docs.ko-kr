---
description: '자세한 정보: 매개 변수 특성'
title: 매개 변수 특성 (c + + COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], parameter attributes
- parameter attributes
ms.assetid: 024c2dd5-49d7-4ced-a17a-c56c1bc485b6
ms.openlocfilehash: f5d0cc2e71ebb77185a5454288c6719636624153
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327430"
---
# <a name="parameter-attributes"></a>매개 변수 특성

다음 특성은 클래스 또는 인터페이스에 있는 메서드의 매개 변수에 적용 됩니다.

|특성|설명|
|---------------|-----------------|
|[재구성](custom-cpp.md)|사용자 고유의 특성을 정의할 수 있습니다.|
|[defaultvalue](defaultvalue.md)|형식화 된 선택적 매개 변수에 기본값을 지정할 수 있습니다.|
|[first_is](first-is.md)|전송할 첫 번째 배열 요소의 인덱스를 지정 합니다.|
|[iid_is](iid-is.md)|전송할 첫 번째 배열 요소의 인덱스를 지정 합니다.|
|[immediatebind](immediatebind.md)|데이터 바인딩된 개체의 속성에 대 한 모든 변경 내용이 데이터베이스에 즉시 전달 됨을 나타냅니다.|
|[in](in-cpp.md)|호출 하는 프로시저에서 호출 되는 프로시저로 매개 변수가 전달 됨을 나타냅니다.|
|[last_is](last-is.md)|전송할 마지막 배열 요소의 인덱스를 지정 합니다.|
|[lcid](lcid.md)|로캘 식별자를 함수에 전달할 수 있습니다.|
|[length_is](length-is.md)|전송할 배열 요소의 수를 지정 합니다.|
|[max_is](max-is.md)|유효한 배열 인덱스에 대 한 최대값을 지정 합니다.|
|[필드](optional-cpp.md)|멤버 함수에 대 한 선택적 매개 변수를 지정 합니다.|
|[out](out-cpp.md)|호출된 프로시저에서 호출하는 프로시저로 반환된(서버에서 클라이언트로 반환된) 포인터 매개 변수를 식별합니다.|
|[range](range-cpp.md)|런타임에 값이 설정 되는 인수 또는 필드에 허용 되는 값 범위를 지정 합니다.|
|[ref](ref-cpp.md)|참조 포인터를 식별 합니다.|
|[retval](retval.md)|멤버의 반환 값을 받는 매개 변수를 지정 합니다.|
|[satype](satype.md)|구조체의 데이터 형식을 지정 합니다 `SAFEARRAY` .|
|[size_is](size-is.md)|크기가 지정 된 포인터에 대해 할당 된 메모리 크기, 크기가 지정 된 포인터에 대 한 포인터 크기 조정 및 단일 또는 다차원 배열을 지정 합니다.|
|[unique](unique-cpp.md)|고유 포인터를 지정 합니다.|

## <a name="see-also"></a>참고 항목

[사용 별 특성](attributes-by-usage.md)
