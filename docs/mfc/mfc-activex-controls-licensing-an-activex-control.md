---
description: '자세한 정보: MFC ActiveX 컨트롤: ActiveX 컨트롤 라이선스'
title: 'MFC ActiveX 컨트롤: ActiveX 컨트롤 라이선스'
ms.date: 11/19/2018
helpviewer_keywords:
- COleObjectFactory class [MFC], licensing controls
- MFC ActiveX controls [MFC], licensing
- VerifyLicenseKey method [MFC]
- VerifyUserLicense method [MFC]
- GetLicenseKey method [MFC]
- licensing ActiveX controls
ms.assetid: cacd9e45-701a-4a1f-8f1f-b0b39f6ac303
ms.openlocfilehash: cf7b797ecfd7ae19af7c922443850d115b4cc2b3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341596"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>MFC ActiveX 컨트롤: ActiveX 컨트롤 라이선스

ActiveX 컨트롤의 선택적 기능인 라이선스 지원을 통해 컨트롤을 사용 하거나 배포할 수 있는 사용자를 제어할 수 있습니다. 라이선스 문제에 대 한 추가 설명은 [기존 ActiveX 컨트롤 업그레이드](upgrading-an-existing-activex-control.md)의 라이선스 문제를 참조 하세요.

> [!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. ActiveX를 대체 하는 최신 기술에 대 한 자세한 내용은 [Activex Controls](activex-controls.md)을 참조 하세요.

이 문서에서는 다음 토픽을 설명합니다.

- [ActiveX 컨트롤 라이선스 개요](#_core_overview_of_activex_control_licensing)

- [사용이 허가 된 컨트롤 만들기](#_core_creating_a_licensed_control)

- [라이선스 지원](#_core_licensing_support)

- [ActiveX 컨트롤의 라이선스 사용자 지정](#_core_customizing_the_licensing_of_an_activex_control)

라이선스를 구현 하는 ActiveX 컨트롤을 사용 하 여 다른 사용자가 ActiveX 컨트롤을 사용 하는 방법을 결정할 수 있습니다. 및 컨트롤을 사용 하 여 제어 구매자를 제공 합니다. LIC 파일 (구매는 구매를 통해 컨트롤을 배포할 수 있지만는 배포할 수 없음). LIC 파일 (컨트롤을 사용 하는 응용 프로그램 포함) 이를 통해 해당 응용 프로그램의 사용자는 먼저 컨트롤에 대 한 라이선스를 부여 하지 않고 컨트롤을 사용 하는 새 응용 프로그램을 작성할 수 없습니다.

## <a name="overview-of-activex-control-licensing"></a><a name="_core_overview_of_activex_control_licensing"></a> ActiveX 컨트롤 라이선스 개요

ActiveX 컨트롤에 대 한 라이선스 지원을 제공 하기 위해 [Coleobjectfactory](reference/coleobjectfactory-class.md) 클래스는 `IClassFactory2` `IClassFactory2::RequestLicKey` , `IClassFactory2::GetLicInfo` 및 인터페이스의 몇 가지 함수에 대 한 구현을 `IClassFactory2::CreateInstanceLic` 제공 합니다. 컨테이너 응용 프로그램 개발자가 컨트롤의 인스턴스를 만들도록 요청 하면 `GetLicInfo` 컨트롤을 확인 하기 위해를 호출 합니다. LIC 파일이 있습니다. 컨트롤이 사용이 허가 되 면 컨트롤의 인스턴스를 만들고 컨테이너에 배치할 수 있습니다. 개발자가 컨테이너 응용 프로그램을 생성 한 후에는이 시간에 대 한 또 다른 함수 호출을 `RequestLicKey` 수행 합니다. 이 함수는 컨테이너 응용 프로그램에 대 한 라이선스 키 (단순 문자열)를 반환 합니다. 그러면 반환 된 키가 응용 프로그램에 포함 됩니다.

아래 그림은 컨테이너 응용 프로그램을 개발 하는 동안 사용 될 ActiveX 컨트롤의 라이선스 확인을 보여 줍니다. 앞에서 설명한 것 처럼 컨테이너 응용 프로그램 개발자에 게는 적절 한가 있어야 합니다. 컨트롤의 인스턴스를 만들기 위해 개발 컴퓨터에 설치 된 LIC 파일입니다.

![허가된 ActiveX 컨트롤이 개발 시 확인됨](../mfc/media/vc374d1.gif "허가된 ActiveX 컨트롤이 개발 시 확인됨") <br/>
개발 도중 사용이 허가된 ActiveX 컨트롤 확인

다음 그림에 표시 된 다음 프로세스는 최종 사용자가 컨테이너 응용 프로그램을 실행할 때 발생 합니다.

응용 프로그램이 시작 되 면 일반적으로 컨트롤의 인스턴스를 만들어야 합니다. 컨테이너는를 호출 하 여 `CreateInstanceLic` 포함 된 라이선스 키를 매개 변수로 전달 하 여이 작업을 수행 합니다. 그러면 포함 된 라이선스 키와 컨트롤 자체의 라이선스 키 복사본 간에 문자열 비교가 수행 됩니다. 일치가 성공적으로 수행 되 면 컨트롤의 인스턴스가 만들어지고 응용 프로그램은 계속 정상적으로 실행 됩니다. 에 유의 하십시오. LIC 파일이 컨트롤 사용자의 컴퓨터에 있을 필요는 없습니다.

![허가된 ActiveX 컨트롤이 실행 시 확인됨](../mfc/media/vc374d2.gif "허가된 ActiveX 컨트롤이 실행 시 확인됨") <br/>
실행 도중 사용이 허가된 ActiveX 컨트롤 확인

컨트롤 라이선스는 컨트롤 구현 DLL의 특정 코드와 라이선스 파일의 두 가지 기본 구성 요소로 구성 됩니다. 코드는 두 개의 함수 호출 및 두 개의 함수 호출로 구성 되며 저작권 표시를 포함 하는 "라이선스 문자열" 이라고 하는 문자열입니다. 이러한 호출과 라이선스 문자열은 컨트롤 구현 ()에서 찾을 수 있습니다. CPP) 파일입니다. ActiveX 컨트롤 마법사에 의해 생성 되는 라이선스 파일은 copyright 문이 포함 된 텍스트 파일입니다. 과 함께 프로젝트 이름을 사용 하 여 이름이 지정 됩니다. LIC 확장 (예: 샘플). .LIC. 사용이 허가 된 컨트롤은 디자인 타임 사용이 필요한 경우 라이선스 파일과 함께 제공 되어야 합니다.

## <a name="creating-a-licensed-control"></a><a name="_core_creating_a_licensed_control"></a> 사용이 허가 된 컨트롤 만들기

ActiveX 컨트롤 마법사를 사용 하 여 컨트롤 프레임 워크를 만드는 경우 라이선스 지원을 포함 하는 것이 쉽습니다. 컨트롤이 런타임 라이선스를 갖도록 지정 하면 ActiveX 컨트롤 마법사는 라이선스를 지원 하기 위해 컨트롤 클래스에 코드를 추가 합니다. 코드는 라이선스 확인을 위해 키와 라이선스 파일을 사용 하는 함수로 구성 됩니다. 이러한 함수를 수정 하 여 컨트롤 라이선스를 사용자 지정할 수도 있습니다. 라이선스 사용자 지정에 대 한 자세한 내용은이 문서의 뒷부분에 있는 [ActiveX 컨트롤의 라이선스 사용자 지정](#_core_customizing_the_licensing_of_an_activex_control) 을 참조 하세요.

#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>컨트롤 프로젝트를 만들 때 ActiveX 컨트롤 마법사를 사용 하 여 라이선스에 대 한 지원을 추가 하려면

1. [MFC ActiveX 컨트롤 만들기](reference/creating-an-mfc-activex-control.md)의 지침을 사용 합니다. ActiveX 컨트롤 마법사의 **응용 프로그램 설정** 페이지에는 런타임 라이선스를 사용 하 여 컨트롤을 만드는 옵션이 포함 되어 있습니다.

이제 ActiveX 컨트롤 마법사는 기본 라이선스 지원을 포함 하는 ActiveX 컨트롤 프레임 워크를 생성 합니다. 라이선스 코드에 대 한 자세한 설명은 다음 항목을 참조 하세요.

## <a name="licensing-support"></a><a name="_core_licensing_support"></a> 라이선스 지원

Activex 컨트롤 마법사를 사용 하 여 ActiveX 컨트롤에 라이선스 지원을 추가 하는 경우 ActiveX 컨트롤 마법사는 라이선스 기능을 선언 하 고 구현 하는 코드를 컨트롤 헤더 및 구현 파일에 추가 합니다. 이 코드는 `VerifyUserLicense` 멤버 함수와 `GetLicenseKey` [Coleobjectfactory](reference/coleobjectfactory-class.md) 에 있는 기본 구현을 재정의 하는 멤버 함수로 구성 됩니다. 이러한 함수는 컨트롤 라이선스를 검색 하 고 확인 합니다.

> [!NOTE]
> 세 번째 멤버 함수는 `VerifyLicenseKey` ActiveX 컨트롤 마법사에서 생성 되지 않지만, 라이선스 키 확인 동작을 사용자 지정 하도록 재정의할 수 있습니다.

이러한 멤버 함수는 다음과 같습니다.

- [VerifyUserLicense](reference/coleobjectfactory-class.md#verifyuserlicense)

   시스템에서 컨트롤 라이선스 파일이 있는지 확인 하 여 컨트롤에서 디자인 타임 사용을 허용 하는지 확인 합니다. 이 함수는 및 처리의 일부로 프레임 워크에서 호출 `IClassFactory2::GetLicInfo` 됩니다 `IClassFactory::CreateInstanceLic` .

- [GetLicenseKey](reference/coleobjectfactory-class.md#getlicensekey)

   컨트롤 DLL에서 고유 키를 요청 합니다. 이 키는 컨테이너 응용 프로그램에 포함 되어 있으며 나중에와 함께 사용 되어 `VerifyLicenseKey` 컨트롤의 인스턴스를 만듭니다. 이 함수는 처리의 일부로 프레임 워크에서 호출 됩니다 `IClassFactory2::RequestLicKey` .

- [VerifyLicenseKey](reference/coleobjectfactory-class.md#verifylicensekey)

   포함 된 키와 컨트롤의 고유 키가 동일한 지 확인 합니다. 이렇게 하면 컨테이너에서 사용할 컨트롤의 인스턴스를 만들 수 있습니다. 이 함수는 처리의 일부로 프레임 워크에서 호출 `IClassFactory2::CreateInstanceLic` 되며 라이선스 키의 사용자 지정 확인을 제공 하도록 재정의할 수 있습니다. 기본 구현에서는 문자열 비교를 수행 합니다. 자세한 내용은이 문서의 뒷부분에 나오는 [ActiveX 컨트롤의 라이선스 사용자 지정](#_core_customizing_the_licensing_of_an_activex_control)을 참조 하세요.

### <a name="header-file-modifications"></a><a name="_core_header_file_modifications"></a> 헤더 파일 수정

ActiveX 컨트롤 마법사는 컨트롤 헤더 파일에 다음 코드를 배치 합니다. 이 예제에서는 `CSampleCtrl` 컨트롤의 존재 여부를 확인 하는 개체의 두 멤버 함수를 `factory` 선언 합니다. LIC 파일 및 컨트롤을 포함 하는 응용 프로그램에 사용할 라이선스 키를 검색 하는 다른 파일입니다.

[!code-cpp[NVC_MFC_AxUI#39](codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]

### <a name="implementation-file-modifications"></a><a name="_core_implementation_file_modifications"></a> 구현 파일 수정

ActiveX 컨트롤 마법사는 컨트롤 구현 파일에 다음 두 개의 문을 배치 하 여 라이선스 파일 이름과 라이선스 문자열을 선언 합니다.

[!code-cpp[NVC_MFC_AxUI#40](codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]

> [!NOTE]
> `szLicString`어떤 방식으로든 수정 하는 경우 컨트롤의 첫 번째 줄도 수정 해야 합니다. LIC 파일 또는 라이선스가 제대로 작동 하지 않습니다.

ActiveX 컨트롤 마법사는 컨트롤 구현 파일에 다음 코드를 배치 하 여 컨트롤 클래스 및 함수를 정의 합니다 `VerifyUserLicense` `GetLicenseKey` .

[!code-cpp[NVC_MFC_AxUI#41](codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]

마지막으로, **ActiveX 컨트롤 마법사** 는 컨트롤 프로젝트를 수정 합니다. IDL 파일. 다음 예제와 같이 **사용이 허가** 된 키워드가 컨트롤의 coclass 선언에 추가 됩니다.

[!code-cpp[NVC_MFC_AxUI#42](codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]

## <a name="customizing-the-licensing-of-an-activex-control"></a><a name="_core_customizing_the_licensing_of_an_activex_control"></a> ActiveX 컨트롤의 라이선스 사용자 지정

`VerifyUserLicense`, `GetLicenseKey` 및 `VerifyLicenseKey` 가 컨트롤 팩터리 클래스의 가상 멤버 함수로 선언 되기 때문에 컨트롤의 라이선스 동작을 사용자 지정할 수 있습니다.

예를 들어 `VerifyUserLicense` 또는 멤버 함수를 재정의 하 여 컨트롤에 대 한 여러 수준의 라이선스를 제공할 수 있습니다 `VerifyLicenseKey` . 이 함수 내에서 검색 한 라이선스 수준에 따라 사용자에 게 노출 되는 속성 또는 메서드를 조정할 수 있습니다.

또한 `VerifyLicenseKey` 사용자에 게 컨트롤 생성 실패를 알리는 사용자 지정 메서드를 제공 하는 코드를 함수에 추가할 수 있습니다. 예를 들어 `VerifyLicenseKey` 멤버 함수에서 컨트롤을 초기화 하지 못했음을 알리는 메시지 상자와 그 이유를 표시할 수 있습니다.

> [!NOTE]
> ActiveX 컨트롤 라이선스 확인을 사용자 지정 하는 다른 방법은를 호출 하는 대신 특정 레지스트리 키에 대 한 등록 데이터베이스를 확인 하는 것입니다 `AfxVerifyLicFile` . 기본 구현에 대 한 예제는이 문서의 [구현 파일 수정](#_core_implementation_file_modifications) 섹션을 참조 하세요.

라이선스 문제에 대 한 추가 설명은 [기존 ActiveX 컨트롤 업그레이드](upgrading-an-existing-activex-control.md)의 라이선스 문제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)<br/>
[MFC ActiveX 컨트롤 마법사](reference/mfc-activex-control-wizard.md)
