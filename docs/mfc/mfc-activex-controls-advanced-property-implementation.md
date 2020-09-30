---
title: 'MFC ActiveX 컨트롤: 고급 속성 구현'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
ms.openlocfilehash: 017959c5809d324af6ab13247fd093a6df280dab
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502209"
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>MFC ActiveX 컨트롤: 고급 속성 구현

이 문서에서는 ActiveX 컨트롤에서 고급 속성을 구현 하는 것과 관련 된 항목을 설명 합니다.

>[!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. ActiveX를 대체 하는 최신 기술에 대 한 자세한 내용은 [Activex Controls](activex-controls.md)을 참조 하세요.

- [읽기 전용 및 쓰기 전용 속성](#_core_read2donly_and_write2donly_properties)

- [속성에서 오류 코드 반환](#_core_returning_error_codes_from_a_property)

## <a name="read-only-and-write-only-properties"></a><a name="_core_read2donly_and_write2donly_properties"></a> 읽기 전용 및 쓰기 전용 속성

속성 추가 마법사는 컨트롤에 대 한 읽기 전용 또는 쓰기 전용 속성을 구현 하는 빠르고 쉬운 방법을 제공 합니다.

#### <a name="to-implement-a-read-only-or-write-only-property"></a>읽기 전용 또는 쓰기 전용 속성을 구현 하려면

1. 컨트롤의 프로젝트를 로드합니다.

1. 클래스 뷰에서 컨트롤의 라이브러리 노드를 확장합니다.

1. 컨트롤의 인터페이스 노드(라이브러리 노드의 두 번째 노드)를 마우스 오른쪽 단추로 클릭하여 바로 가기 메뉴를 엽니다.

1. 바로 가기 메뉴에서 **추가** 를 클릭 한 다음 **속성 추가**를 클릭 합니다.

   그러면 [속성 추가 마법사](../ide/adding-a-property-visual-cpp.md#names-add-property-wizard)가 열립니다.

1. **속성 이름** 상자에 속성의 이름을 입력 합니다.

1. **구현 형식**에서 **Get/Set 메서드**를 클릭합니다.

1. **속성 유형** 상자에서 속성에 대 한 적절 한 유형을 선택 합니다.

1. 읽기 전용 속성을 원하는 경우 Set 함수 이름을 지우십시오. 쓰기 전용 속성을 원하는 경우 Get 함수 이름을 지웁니다.

1. **Finish**를 클릭합니다.

이 작업을 수행 하면 속성 추가 마법사가 함수 `SetNotSupported` 또는 `GetNotSupported` 디스패치 맵 항목을 일반 Set 또는 Get 함수 대신 삽입 합니다.

기존 속성을 읽기 전용 또는 쓰기 전용으로 변경 하려는 경우 디스패치 맵을 수동으로 편집 하 고 컨트롤 클래스에서 불필요 한 Set 또는 Get 함수를 제거할 수 있습니다.

속성이 조건부로 읽기 전용 이거나 쓰기 전용으로 설정 하려는 경우 (예: 컨트롤이 특정 모드에서 작동 하는 경우에만) Set 또는 Get 함수를 정상적으로 제공 하 고 또는 함수를 적절 하 게 호출할 수 있습니다 `SetNotSupported` `GetNotSupported` . 다음은 그 예입니다.

[!code-cpp[NVC_MFC_AxUI#29](codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]

이 코드 샘플 `SetNotSupported` `m_bReadOnlyMode` 은 데이터 멤버가 **TRUE**인 경우를 호출 합니다. **FALSE**이면 속성이 새 값으로 설정 됩니다.

## <a name="returning-error-codes-from-a-property"></a><a name="_core_returning_error_codes_from_a_property"></a> 속성에서 오류 코드 반환

속성을 가져오거나 설정 하려고 시도 하는 동안 오류가 발생 했음을 나타내려면를 매개 변수로 사용 하 `COleControl::ThrowError` 는 함수를 사용 합니다 (상태 코드). 미리 정의 된을 사용 하거나 고유한 항목 중 하나를 정의할 수 있습니다. 사용자 지정 코드를 정의 하는 미리 정의 된 SCODEs의 목록과 지침은 activex 컨트롤: 고급 항목에서 [Activex 컨트롤의 오류 처리](mfc-activex-controls-advanced-topics.md) 를 참조 하세요.

[Colecontrol:: SetNotSupported](reference/colecontrol-class.md#setnotsupported), [Colecontrol:: getnotsupported](reference/colecontrol-class.md#getnotsupported)및 [colecontrol:: setnotsupported](reference/colecontrol-class.md#setnotpermitted)와 같은 가장 일반적으로 미리 정의 된 scodes에 대 한 도우미 함수가 있습니다.

> [!NOTE]
> `ThrowError` 는 속성의 Get 또는 Set 함수 또는 자동화 메서드 내에서 오류를 반환 하는 수단 으로만 사용 됩니다. 이러한 경우에는 적절 한 예외 핸들러가 스택에 표시 됩니다.

코드의 다른 영역에서 예외를 보고 하는 방법에 대 한 자세한 내용은 ActiveX 컨트롤: 고급 항목 문서에서 [COleControl:: FireError](reference/colecontrol-class.md#fireerror) 및 [Activex 컨트롤에서 오류 처리](mfc-activex-controls-advanced-topics.md) 섹션을 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)<br/>
[MFC ActiveX 컨트롤: 속성](mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 컨트롤: 메서드](mfc-activex-controls-methods.md)<br/>
[COleControl 클래스](reference/colecontrol-class.md)
