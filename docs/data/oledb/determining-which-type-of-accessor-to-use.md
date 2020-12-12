---
description: '자세한 정보: 사용할 접근자 형식 결정'
title: 사용할 접근자 형식 결정
ms.date: 05/09/2019
helpviewer_keywords:
- rowsets [C++], data types
- accessors [C++], types
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
ms.openlocfilehash: f41a39e4920fa68ed901c3b33ad71a0ddd3cf8c3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287595"
---
# <a name="determining-which-type-of-accessor-to-use"></a>사용할 접근자 형식 결정

컴파일 시간 또는 런타임에 행 집합의 데이터 형식을 확인할 수 있습니다.

컴파일 시간에 데이터 형식을 확인해야 하는 경우 정적 접근자(예: `CAccessor`)를 사용합니다.

런타임에 데이터 형식을 확인해야 하는 경우 동적 접근자(`CDynamicAccessor` 또는 자식) 또는 수동 접근자(`CManualAccessor`)를 사용합니다. 이러한 경우, 행 집합에서 `GetColumnInfo`를 호출하여 열 바인딩 정보를 반환할 수 있으며, 이 정보를 통해 형식을 확인할 수 있습니다.

다음 표에는 소비자 템플릿에서 제공되는 접근자 형식이 나와 있습니다. 접근자마다 장단점이 있습니다. 상황에 따라 요구에 적합한 접근자 형식이 다릅니다.

|접근자 클래스|바인딩|매개 변수|의견|
|--------------------|-------------|---------------|-------------|
|`CAccessor`|COLUMN_ENTRY 매크로를 사용하여 사용자 레코드를 만듭니다. 이 매크로는 해당 레코드의 데이터 멤버를 접근자에 바인딩합니다. 행 집합을 만들 때는 열 바인딩을 해제할 수 없습니다.|예(PARAM_MAP 매크로 항목 사용). 바인딩한 후에는 매개 변수 바인딩을 해제할 수 없습니다.|코드 양이 적기 때문에 가장 빠른 접근자입니다.|
|`CDynamicAccessor`|자동.|아니요.|행 집합의 데이터 형식을 알 수 없는 경우에 유용합니다.|
|`CDynamicParameterAccessor`|자동이지만, [재정의](../../data/oledb/overriding-a-dynamic-accessor.md)할 수 있습니다.|예(공급자가 `ICommandWithParameters`를 지원하는 경우). 매개 변수가 자동으로 바인딩됩니다.|`CDynamicAccessor`보다 느리지만, 제네릭 저장 프로시저를 호출하는 데 유용합니다.|
|`CDynamicStringAccessor[A,W]`|자동.|아니요.|데이터 저장소에서 액세스된 데이터를 문자열 데이터로 검색합니다.|
|`CManualAccessor`|수동(`AddBindEntry` 사용).|수동(`AddParameterEntry` 사용).|빠르고, 매개 변수와 열이 한 번만 바인딩됩니다. 사용할 데이터 형식을 직접 결정합니다. 예는 [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) 샘플을 참조 하세요. 또는 보다 더 많은 코드가 필요 `CDynamicAccessor` `CAccessor` 합니다. OLE DB를 직접 호출하는 것과 같습니다.|
|`CXMLAccessor`|자동.|아니요.|데이터 저장소에서 액세스된 데이터를 문자열 데이터로 검색하고, XML 태그 데이터로 서식을 지정합니다.|

## <a name="see-also"></a>참고 항목

[접근자 사용](../../data/oledb/using-accessors.md)
