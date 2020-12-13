---
description: '자세한 정보: MFC ActiveX 컨트롤: ActiveX 컨트롤 지역화'
title: 'MFC ActiveX 컨트롤: ActiveX 컨트롤 지역화'
ms.date: 09/12/2018
f1_keywords:
- LocaleID
- AfxOleRegisterTypeLib
helpviewer_keywords:
- localization, ActiveX controls
- MFC ActiveX controls [MFC], localizing
- LocaleID ambient property [MFC]
- LOCALIZE sample [MFC]
ms.assetid: a44b839a-c652-4ec5-b824-04392708a5f9
ms.openlocfilehash: 830fecd316b48f61da4f90136dd29455801ec725
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150217"
---
# <a name="mfc-activex-controls-localizing-an-activex-control"></a>MFC ActiveX 컨트롤: ActiveX 컨트롤 지역화

이 문서에서는 ActiveX 컨트롤 인터페이스를 지역화 하는 절차에 대해 설명 합니다.

>[!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. ActiveX를 대체 하는 최신 기술에 대 한 자세한 내용은 [Activex Controls](activex-controls.md)을 참조 하세요.

ActiveX 컨트롤을 국제 시장에 맞게 조정 하려는 경우 컨트롤을 지역화할 수 있습니다. Windows는 독일어, 프랑스어 및 스웨덴어를 비롯 한 기본 영어 외에도 다양 한 언어를 지원 합니다. 이는 해당 인터페이스가 영어로만 된 경우 컨트롤에 대 한 문제를 나타낼 수 있습니다.

일반적으로 ActiveX 컨트롤은 앰비언트 LocaleID 속성에서 항상 로캘을 기반으로 해야 합니다. 이때 다음과 같은 세 가지 방법을 사용할 수 있습니다.

- 앰비언트 LocaleID 속성의 현재 값을 기반으로 하 여 항상 주문형 리소스를 로드 합니다. MFC ActiveX 컨트롤 샘플 [지역화](../overview/visual-cpp-samples.md) 는이 전략을 사용 합니다.

- 첫 번째 컨트롤이 인스턴스화된 경우 앰비언트 LocaleID 속성을 기반으로 리소스를 로드 하 고 다른 모든 인스턴스에 대해 이러한 리소스를 사용 합니다. 이 문서에서는 이러한 전략을 보여 줍니다.

    > [!NOTE]
    >  일부 경우에는 이후 인스턴스에 다른 로캘이 있는 경우 제대로 작동 하지 않습니다.

- `OnAmbientChanged`알림 함수를 사용 하 여 컨테이너 로캘로 적절 한 리소스를 동적으로 로드 합니다.

    > [!NOTE]
    >  이는 컨트롤에 대해 작동 하지만, 앰비언트 LocaleID 속성이 변경 될 때 런타임 DLL은 동적으로 자체 리소스를 업데이트 하지 않습니다. 또한 ActiveX 컨트롤에 대 한 런타임 Dll은 스레드 로캘을 사용 하 여 해당 리소스에 대 한 로캘을 결정 합니다.

이 문서의 나머지 부분에서는 두 가지 지역화 전략에 대해 설명 합니다. 첫 번째 전략은 [컨트롤의 프로그래밍 인터페이스](#_core_localizing_your_control.92.s_programmability_interface) (속성, 메서드 및 이벤트 이름)를 문제의 합니다. 두 번째 전략은 컨테이너의 앰비언트 LocaleID 속성을 사용 하 여 [컨트롤의 사용자 인터페이스를 문제의](#_core_localizing_the_control.92.s_user_interface)합니다. 컨트롤 지역화에 대 한 데모는 MFC ActiveX 컨트롤 샘플 [지역화](../overview/visual-cpp-samples.md)를 참조 하세요.

## <a name="localizing-the-controls-programmability-interface"></a><a name="_core_localizing_your_control.92.s_programmability_interface"></a> 컨트롤의 프로그래밍 인터페이스 지역화

컨트롤의 프로그래밍 인터페이스 (프로그래머가 컨트롤을 사용 하는 응용 프로그램을 작성 하는 데 사용 하는 인터페이스)를 지역화할 때 컨트롤의 수정 된 버전을 만들어야 합니다. 지원 하려는 각 언어에 대 한 IDL 파일 (컨트롤 형식 라이브러리를 빌드하기 위한 스크립트)입니다. 이는 컨트롤 속성 이름을 지역화 하는 데 필요한 유일한 장소입니다.

지역화 된 컨트롤을 개발 하는 경우 로캘 ID를 형식 라이브러리 수준에서 특성으로 포함 합니다. 예를 들어, 프랑스어로 지역화 된 속성 이름으로 형식 라이브러리를 제공 하려는 경우 샘플의 복사본을 만듭니다. IDL 파일을 호출 하 고이를 호출 합니다. IDL. 다음과 같이 로캘 ID 특성을 파일에 추가 합니다 (프랑스어의 로캘 ID는 0x040c).

[!code-cpp[NVC_MFC_AxLoc#1](codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_1.idl)]

SAMPLEFR에서 속성 이름을 변경 합니다. 해당 프랑스어에 해당 하는 IDL로 이동한 다음 MKTYPLIB.EXE을 사용 하 여 프랑스어 형식 라이브러리 SAMPLEFR을 생성 합니다. TLB.

지역화 된 형식 라이브러리를 여러 개 만들려면 지역화 된 형식 라이브러리를 추가할 수 있습니다. IDL 파일은 프로젝트에 자동으로 빌드됩니다.

#### <a name="to-add-an-idl-file-to-your-activex-control-project"></a>를 추가 합니다. ActiveX 컨트롤 프로젝트에 대 한 IDL 파일

1. 컨트롤 프로젝트를 열고 **프로젝트** 메뉴에서 **기존 항목 추가** 를 클릭 합니다.

   **기존 항목 추가** 대화 상자가 나타납니다.

1. 필요한 경우 확인할 드라이브 및 디렉터리를 선택 합니다.

1. **파일 형식** 상자에서 **모든 파일 ( \* . \* )** 을 선택 합니다.

1. 파일 목록 상자에서을 두 번 클릭 합니다. 프로젝트에 삽입 하려는 IDL 파일입니다.

1. 필요한 모든를 추가 했으면 **열기** 를 클릭 합니다. IDL 파일.

프로젝트에 추가 된 파일은 프로젝트의 나머지 부분을 빌드할 때 빌드됩니다. 지역화 된 형식 라이브러리는 현재 ActiveX 컨트롤 프로젝트 디렉터리에 있습니다.

코드 내에서 내부 속성 이름 (일반적으로 영어)은 항상 사용 되며 지역화 되지 않습니다. 여기에는 컨트롤 디스패치 맵, 속성 교환 함수 및 속성 페이지 데이터 교환 코드가 포함 됩니다.

하나의 형식 라이브러리 (. TLB) 파일은 컨트롤 구현 ()의 리소스에 바인딩될 수 있습니다. OCX) 파일입니다. 일반적으로 표준화 된 (일반적으로, 영어) 이름을 사용 하는 버전입니다. 컨트롤의 지역화 된 버전을 제공 하려면를 제공 해야 합니다. OCX (이미 기본값에 바인딩 됨) TLB 버전) 및입니다. 적절 한 로캘에 대 한 TLB. 이는만을 의미 합니다. OCX는 올바른 이후 영어 버전에 필요 합니다. TLB가 이미 바인딩되어 있습니다. 다른 로캘의 경우 지역화 된 형식 라이브러리도와 함께 제공 되어야 합니다. OCX.

컨트롤의 클라이언트가 지역화 된 형식 라이브러리를 찾을 수 있도록 하려면 로캘 관련를 등록 합니다. Windows 시스템 레지스트리의 TypeLib 섹션에서 TLB 파일을 삭제 합니다. 이 목적을 위해 [AfxOleRegisterTypeLib](reference/registering-ole-controls.md#afxoleregistertypelib) 함수의 세 번째 매개 변수 (일반적으로 선택 사항)가 제공 됩니다. 다음 예제에서는 ActiveX 컨트롤에 대 한 프랑스어 형식 라이브러리를 등록 합니다.

[!code-cpp[NVC_MFC_AxLoc#2](codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_2.cpp)]

컨트롤이 등록 되 면 `AfxOleRegisterTypeLib` 함수는 지정 된를 자동으로 찾습니다. 컨트롤과 동일한 디렉터리에 있는 TLB 파일을 Windows 등록 데이터베이스에 등록 합니다. 이면이 고, 그렇지 않으면입니다. TLB 파일이 없으므로 함수는 영향을 주지 않습니다.

## <a name="localizing-the-controls-user-interface"></a><a name="_core_localizing_the_control.92.s_user_interface"></a> 컨트롤의 사용자 인터페이스 지역화

컨트롤의 사용자 인터페이스를 지역화 하려면 모든 컨트롤의 사용자가 볼 수 있는 리소스 (예: 속성 페이지 및 오류 메시지)를 언어별 리소스 Dll에 저장 합니다. 그런 다음 컨테이너의 앰비언트 LocaleID 속성을 사용 하 여 사용자의 로캘에 적합 한 DLL을 선택할 수 있습니다.

다음 코드 예제에서는 특정 로캘에 대 한 리소스 DLL을 찾아서 로드 하는 한 가지 방법을 보여 줍니다. 이 예제에 대해 호출 되는이 멤버 함수 `GetLocalizedResourceHandle` 는 ActiveX 컨트롤 클래스의 멤버 함수 일 수 있습니다.

[!code-cpp[NVC_MFC_AxLoc#3](codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_3.cpp)]

Switch 문의 각 사례에서 하위 언어 ID를 확인 하 여 보다 특수화 된 지역화를 제공할 수 있습니다. 이 함수에 대 한 데모를 보려면 `GetResourceHandle` MFC ActiveX 컨트롤 샘플 [지역화](../overview/visual-cpp-samples.md)에서 함수를 참조 하세요.

컨트롤이 먼저 컨테이너에 로드 되는 경우 [COleControl:: AmbientLocaleID](reference/colecontrol-class.md#ambientlocaleid) 를 호출 하 여 로캘 ID를 검색할 수 있습니다. 그런 다음이 컨트롤은 `GetLocalizedResourceHandle` 적절 한 리소스 라이브러리를 로드 하는 함수에 반환 된 로캘 ID 값을 전달할 수 있습니다. 컨트롤은 결과 핸들 (있는 경우)을 [AfxSetResourceHandle](reference/application-information-and-management.md#afxsetresourcehandle)에 전달 해야 합니다.

[!code-cpp[NVC_MFC_AxLoc#4](codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_4.cpp)]

위의 코드 샘플을 [COleControl:: OnSetClientSite](reference/colecontrol-class.md#onsetclientsite)의 재정의와 같이 컨트롤의 멤버 함수에 추가 합니다. 또한 *m_hResDLL* 은 컨트롤 클래스의 멤버 변수 여야 합니다.

컨트롤의 속성 페이지를 지역화 하는 데 유사한 논리를 사용할 수 있습니다. 속성 페이지를 지역화 하려면 다음 샘플과 비슷한 코드를 속성 페이지의 구현 파일 ( [COlePropertyPage:: OnSetPageSite](reference/colepropertypage-class.md#onsetpagesite)의 재정의)에 추가 합니다.

[!code-cpp[NVC_MFC_AxLoc#5](codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_5.cpp)]

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)
