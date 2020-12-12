---
description: '자세한 정보: ActiveX 컨트롤 컨테이너: ActiveX 컨트롤 포함 수동 사용'
title: 'ActiveX 컨트롤 컨테이너: ActiveX 컨트롤 포함 수동 설정'
ms.date: 09/12/2018
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
ms.openlocfilehash: 44ca8961b064aee1efd4a24dd5bf6841399131e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277962"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>ActiveX 컨트롤 컨테이너: ActiveX 컨트롤 포함 수동 설정

MFC 응용 프로그램 마법사를 사용 하 여 응용 프로그램을 생성할 때 ActiveX 컨트롤 지원을 사용 하도록 설정 하지 않은 경우에는이 지원을 수동으로 추가 해야 합니다. 이 문서에서는 기존 OLE 컨테이너 응용 프로그램에 ActiveX 컨트롤 포함을 수동으로 추가 하는 프로세스에 대해 설명 합니다. OLE 컨테이너에서 ActiveX 컨트롤을 지 원하는 것을 미리 알고 있는 경우에는 [MFC Activex 컨트롤 컨테이너 만들기](reference/creating-an-mfc-activex-control-container.md)문서를 참조 하세요.

>[!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. ActiveX를 대체 하는 최신 기술에 대 한 자세한 내용은 [Activex Controls](activex-controls.md)을 참조 하세요.

> [!NOTE]
> 이 문서에서는 프로시저 및 코드에서 예제로 이름이 Container 이라는 대화 상자 기반 ActiveX 컨트롤 컨테이너 프로젝트와 Circ 라는 포함 된 컨트롤을 사용 합니다.

ActiveX 컨트롤을 지원 하려면 프로젝트의 두 파일에 코드 줄 하나를 추가 해야 합니다.

- 컨테이너에 있는 기본 대화 상자의 기능을 수정 `InitInstance` 합니다. 다음 예제와 같이 [AfxEnableControlContainer](reference/ole-initialization.md#afxenablecontrolcontainer)를 호출 하는 MFC 응용 프로그램 마법사를 통해 CPP를 호출 합니다.

   [!code-cpp[NVC_MFCOleContainer#34](codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]
    [!code-cpp[NVC_MFCOleContainer#35](codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]

- 프로젝트의 STDAFX.H에 다음을 추가 합니다. H 헤더 파일 (H):

   [!code-cpp[NVC_MFCOleContainer#36](codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]

이러한 단계를 완료 한 후 **빌드** 메뉴에서 **빌드** 를 클릭 하 여 프로젝트를 다시 빌드합니다.

## <a name="see-also"></a>참고 항목

[ActiveX 컨트롤 컨테이너](activex-control-containers.md)
