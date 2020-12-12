---
description: '자세한 정보: COM 특성'
title: COM 특성
ms.date: 10/03/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- attributes [COM]
- COM, attributes
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
ms.openlocfilehash: d1377bdcb449190d01f529b2a4c713f138cbef5f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269174"
---
# <a name="com-attributes"></a>COM 특성

COM 특성은 COM 개발의 다양 한 영역을 지원 하 고 공용 언어 런타임 개발을 .NET Framework 하는 코드를 삽입 합니다. 이러한 영역은 사용자 지정 인터페이스 구현에서 스톡 속성, 메서드 및 이벤트를 지원 하기 위해 기존 인터페이스를 지원 합니다. 또한 복합 및 ActiveX 컨트롤 구현에 대 한 지원을 찾을 수 있습니다.

|특성|설명|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|다른 컨트롤에서 컨트롤을 집계할 수 있음을 나타냅니다.|
|[집계](aggregates.md)|컨트롤이 대상 클래스를 집계 함을 나타냅니다.|
|[coclass](coclass.md)|Com 인터페이스를 구현할 수 있는 COM 개체를 만듭니다.|
|[com_interface_entry](com-interface-entry-cpp.md)|인터페이스 항목을 COM 맵에 추가 합니다.|
|[implements_category](implements-category.md)|클래스에 대해 구현 된 구성 요소 범주를 지정 합니다.|
|[progid](progid.md)|컨트롤의 ProgID를 정의 합니다.|
|[rdx](rdx.md)|레지스트리 키를 만들거나 수정 합니다.|
|[registration_script](registration-script.md)|지정 된 등록 스크립트를 실행 합니다.|
|[requires_category](requires-category.md)|클래스에 대 한 필수 구성 요소 범주를 지정 합니다.|
|[support_error_info](support-error-info.md)|대상 개체에 대 한 오류 보고를 지원 합니다.|
|[항목과](synchronize.md)|메서드에 대 한 액세스를 동기화 합니다.|
|[스레딩을](threading-cpp.md)|COM 개체의 스레딩 모델을 지정 합니다.|
|[vi_progid](vi-progid.md)|컨트롤에 대 한 버전 독립 ProgID를 정의 합니다.|

## <a name="see-also"></a>참고 항목

[그룹별 특성](attributes-by-group.md)
