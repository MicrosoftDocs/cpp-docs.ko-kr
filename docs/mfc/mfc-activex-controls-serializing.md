---
description: '자세한 정보: MFC ActiveX 컨트롤: Serialize'
title: 'MFC ActiveX 컨트롤: Serialize'
ms.date: 09/12/2018
f1_keywords:
- _wVerMinor
- DoPropExchange
- _wVerMajor
helpviewer_keywords:
- MFC ActiveX controls [MFC], version support
- wVerMinor global constant [MFC]
- GetVersion method [MFC]
- ExchangeVersion method [MFC]
- MFC ActiveX controls [MFC], serializing
- DoPropExchange method [MFC]
- versioning ActiveX controls
- wVerMajor global constant
ms.assetid: 9d57c290-dd8c-4853-b552-6f17f15ebedd
ms.openlocfilehash: 24f49aa1dfb37c6ac981035f33d0f60e6fa398f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206047"
---
# <a name="mfc-activex-controls-serializing"></a>MFC ActiveX 컨트롤: Serialize

이 문서에서는 ActiveX 컨트롤을 serialize 하는 방법을 설명 합니다. Serialization은 디스크 파일 등의 영구 저장소 미디어에서 읽거나 쓰는 프로세스입니다. MFC (Microsoft Foundation Class) 라이브러리는 클래스의 serialization에 대 한 기본 제공 지원을 제공 합니다 `CObject` . `COleControl` 속성 교환 메커니즘을 사용 하 여이 지원을 ActiveX 컨트롤에 확장 합니다.

>[!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. ActiveX를 대체 하는 최신 기술에 대 한 자세한 내용은 [Activex Controls](activex-controls.md)을 참조 하세요.

ActiveX 컨트롤에 대 한 Serialization은 [COleControl::D oPropExchange](reference/colecontrol-class.md#dopropexchange)를 재정의 하 여 구현 됩니다. 컨트롤 개체를 로드 하 고 저장 하는 동안 호출 되는이 함수는 멤버 변수 또는 변경 알림이 포함 된 멤버 변수를 사용 하 여 구현 된 모든 속성을 저장 합니다.

다음 항목에서는 ActiveX 컨트롤을 serialize 하는 것과 관련 된 주요 문제를 다룹니다.

- `DoPropExchange`컨트롤 개체를 serialize 하는 함수 구현

- [Serialization 프로세스 사용자 지정](#_core_customizing_the_default_behavior_of_dopropexchange)

- [버전 지원 구현](#_core_implementing_version_support)

## <a name="implementing-the-dopropexchange-function"></a><a name="_core_implementing_the_dopropexchange_function"></a> DoPropExchange 함수 구현

ActiveX 컨트롤 마법사를 사용 하 여 컨트롤 프로젝트를 생성 하는 경우에는 [COleControl::D oPropExchange](reference/colecontrol-class.md#dopropexchange)의 기본 구현을 비롯 하 여 몇 가지 기본 처리기 함수가 컨트롤 클래스에 자동으로 추가 됩니다. 다음 예제에서는 ActiveX 컨트롤 마법사를 사용 하 여 만든 클래스에 추가 된 코드를 보여 줍니다.

[!code-cpp[NVC_MFC_AxUI#43](codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]

속성을 영구적으로 설정 하려면 `DoPropExchange` 속성 교환 함수에 대 한 호출을 추가 하 여을 수정 합니다. 다음 예제에서는 사용자 지정 부울 CircleShape 속성의 serialization을 보여 줍니다. 여기서 CircleShape 속성의 기본값은 **TRUE** 입니다.

[!code-cpp[NVC_MFC_AxSer#1](codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#2](codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]

다음 표에서는 컨트롤의 속성을 serialize 하는 데 사용할 수 있는 속성 교환 함수를 보여 줍니다.

|속성 교환 함수|목적|
|---------------------------------|-------------|
|**PX_Blob ()**|형식 BLOB (Binary Large Object) 데이터 속성을 serialize 합니다.|
|**PX_Bool ()**|형식 부울 속성을 serialize 합니다.|
|**PX_Color ()**|형식 색 속성을 serialize 합니다.|
|**PX_Currency ()**|**CY** (currency) 형식 속성을 serialize 합니다.|
|**PX_Double ()**|형식 속성을 serialize **`double`** 합니다.|
|**PX_Font ()**|글꼴 형식 속성을 serialize 합니다.|
|**PX_Float ()**|형식 속성을 serialize **`float`** 합니다.|
|**PX_IUnknown ()**|형식의 속성을 serialize `LPUNKNOWN` 합니다.|
|**PX_Long ()**|형식 속성을 serialize **`long`** 합니다.|
|**PX_Picture ()**|형식 그림 속성을 serialize 합니다.|
|**PX_Short ()**|형식 속성을 serialize **`short`** 합니다.|
|**PXstring ()**|형식 속성을 serialize `CString` 합니다.|
|**PX_ULong ()**|**ULONG** 속성 형식을 serialize 합니다.|
|**PX_UShort ()**|**USHORT** 속성 형식을 serialize 합니다.|

이러한 속성 교환 함수에 대 한 자세한 내용은 *MFC 참조* 에서 [OLE 컨트롤의 지 속성](reference/persistence-of-ole-controls.md) 을 참조 하세요.

## <a name="customizing-the-default-behavior-of-dopropexchange"></a><a name="_core_customizing_the_default_behavior_of_dopropexchange"></a> DoPropExchange의 기본 동작 사용자 지정

이전 항목과 같이의 기본 구현에서는 `DoPropertyExchange` 기본 클래스를 호출 합니다 `COleControl` . 그러면에서 자동으로 지원 되는 속성 집합이 serialize 되어 `COleControl` 컨트롤의 사용자 지정 속성만 직렬화 하는 것 보다 더 많은 저장 공간을 사용 합니다. 이 호출을 제거 하면 중요 한 것으로 생각 되는 속성만 개체에서 serialize 할 수 있습니다. 컨트롤에 구현 된 모든 스톡 속성 상태는 명시적으로 **PX_** 호출을 추가 하지 않는 한 컨트롤 개체를 저장 하거나 로드할 때 serialize 되지 않습니다.

## <a name="implementing-version-support"></a><a name="_core_implementing_version_support"></a> 버전 지원 구현

버전 지원을 통해 수정 된 ActiveX 컨트롤을 사용 하 여 새 영구 속성을 추가 하 고 이전 버전의 컨트롤에서 만든 영구 상태를 검색 하 고 로드할 수 있습니다. 컨트롤의 버전을 영구 데이터의 일부로 사용할 수 있도록 하려면 컨트롤의 함수에서 [COleControl:: ExchangeVersion](reference/colecontrol-class.md#exchangeversion) 를 호출 `DoPropExchange` 합니다. Activex 컨트롤 마법사를 사용 하 여 ActiveX 컨트롤을 만든 경우에는이 호출이 자동으로 삽입 됩니다. 버전 지원이 필요 하지 않은 경우 제거할 수 있습니다. 그러나 컨트롤 크기의 비용은 버전 지원에서 제공 하는 추가 유연성을 위해 매우 작습니다 (4 바이트).

ActiveX 컨트롤 마법사를 사용 하 여 컨트롤을 만들지 않은 경우를 `COleControl::ExchangeVersion` `DoPropExchange` 호출 하기 전에 함수 시작 부분에 다음 줄을 삽입 하 여에 대 한 호출을 추가 합니다 `COleControl::DoPropExchange` .

[!code-cpp[NVC_MFC_AxSer#1](codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

버전 번호로 **DWORD** 를 사용할 수 있습니다. ActiveX 컨트롤 마법사에 의해 생성 된 프로젝트는 `_wVerMinor` 및를 `_wVerMajor` 기본값으로 사용 합니다. 이러한 상수는 프로젝트의 ActiveX 컨트롤 클래스의 구현 파일에 정의 된 전역 상수입니다. 함수의 나머지 부분 내에서 언제 `DoPropExchange` 든 지 [Cpropexchange:: GetVersion](reference/cpropexchange-class.md#getversion) 를 호출 하 여 저장 하거나 검색 하는 버전을 검색할 수 있습니다.

다음 예제에서이 샘플 컨트롤의 버전 1에는 "ReleaseDate" 속성만 있습니다. 버전 2는 "OriginalDate" 속성을 추가 합니다. 이전 버전에서 영구 상태를 로드 하도록 컨트롤에 지시 하는 경우 새 속성에 대 한 멤버 변수를 기본값으로 초기화 합니다.

[!code-cpp[NVC_MFC_AxSer#4](codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

기본적으로 "컨트롤은 이전 데이터를 최신 형식으로 변환 합니다. 예를 들어, 컨트롤의 버전 2가 버전 1에서 저장 한 데이터를 로드 하는 경우 다시 저장할 때 버전 2 형식을 작성 합니다. 컨트롤이 마지막으로 읽은 형식으로 데이터를 저장 하도록 하려면를 호출할 때 **FALSE** 를 세 번째 매개 변수로 전달 `ExchangeVersion` 합니다. 이 세 번째 매개 변수는 선택 사항이 며 기본적으로 **TRUE** 입니다.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)
