---
description: '자세한 정보: MFC ActiveX 컨트롤: 스톡 속성 페이지 사용'
title: 'MFC ActiveX 컨트롤: 스톡 속성 페이지 사용'
ms.date: 09/12/2018
f1_keywords:
- CLSID_CPicturePropPage
- CLSID_CColorPropPage
- CLSID_CFontPropPage
helpviewer_keywords:
- picture stock property pages [MFC]
- CLSID_CFontPropPage [MFC]
- color stock property pages [MFC]
- CLSID_CColorPropPage [MFC]
- fonts [MFC], ActiveX controls
- stock properties [MFC], stock property pages
- CLSID_CPicturePropPage [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 22638d86-ff3e-4124-933e-54b7c2a25968
ms.openlocfilehash: 37cb6e5b5dfa08c5e7935064a66c2c77fe8dcde6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97133057"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>MFC ActiveX 컨트롤: 스톡 속성 페이지 사용

이 문서에서는 ActiveX 컨트롤에 사용할 수 있는 스톡 속성 페이지와이를 사용 하는 방법에 대해 설명 합니다.

>[!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. ActiveX를 대체 하는 최신 기술에 대 한 자세한 내용은 [Activex Controls](activex-controls.md)을 참조 하세요.

ActiveX 컨트롤에서 속성 페이지를 사용 하는 방법에 대 한 자세한 내용은 다음 문서를 참조 하세요.

- [MFC ActiveX 컨트롤: 속성 페이지](mfc-activex-controls-property-pages.md)

- [MFC ActiveX 컨트롤: 다른 사용자 지정 속성 페이지 추가](mfc-activex-controls-adding-another-custom-property-page.md)

MFC는 ActiveX 컨트롤에 사용할 세 가지 스톡 속성 페이지,, 및를 제공 `CLSID_CColorPropPage` `CLSID_CFontPropPage` `CLSID_CPicturePropPage` 합니다. 이러한 페이지에는 각각 스톡 색, 글꼴 및 그림 속성에 대 한 사용자 인터페이스가 표시 됩니다.

이러한 속성 페이지를 컨트롤에 통합 하려면 컨트롤의 속성 페이지 Id 배열을 초기화 하는 코드에 해당 Id를 추가 합니다. 다음 예제에서이 코드는 제어 구현 파일 ()에 있습니다. CPP)는 세 개의 스톡 속성 페이지와 기본 속성 페이지 (이 예제에서는 이름)를 모두 포함 하도록 배열을 초기화 합니다 `CMyPropPage` .

[!code-cpp[NVC_MFC_AxOpt#21](codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]

BEGIN_PROPPAGEIDS 매크로의 속성 페이지 수는 4입니다. ActiveX 컨트롤에서 지 원하는 속성 페이지 수를 나타냅니다.

이러한 수정 내용을 적용 한 후 프로젝트를 다시 빌드합니다. 이제 컨트롤에 글꼴, 그림 및 색 속성에 대 한 속성 페이지가 있습니다.

> [!NOTE]
> 컨트롤 스톡 속성 페이지에 액세스할 수 없는 경우 MFC DLL (MFCxx.DLL)이 현재 운영 체제에 제대로 등록 되지 않았기 때문일 수 있습니다. 이는 일반적으로 현재 실행 중인 운영 체제와 다른 운영 체제에서 Visual C++을 설치 하는 것입니다.

> [!TIP]
> 스톡 속성 페이지가 표시 되지 않는 경우 (이전 참고 참조) dll의 전체 경로 이름을 사용 하 여 명령줄에서 RegSvr32.exe를 실행 하 여 DLL을 등록 합니다.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)<br/>
[MFC ActiveX 컨트롤: 스톡 속성 추가](mfc-activex-controls-adding-stock-properties.md)
