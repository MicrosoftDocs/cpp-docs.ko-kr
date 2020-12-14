---
description: '자세한 정보: MFC ActiveX 컨트롤: 자동화 서버 만들기'
title: 'MFC ActiveX 컨트롤: 자동화 서버 만들기'
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers [MFC], MFC ActiveX controls
- ActiveX controls [MFC], Automation server
- MFC ActiveX controls [MFC], Automation server
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
ms.openlocfilehash: ffac05d48a17e0f8b40f268709393fff392a3b95
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280731"
---
# <a name="mfc-activex-controls-creating-an-automation-server"></a>MFC ActiveX 컨트롤: 자동화 서버 만들기

다른 응용 프로그램에서 프로그래밍 방식으로 컨트롤을 포함 하 고 응용 프로그램에서 컨트롤의 메서드를 호출 하는 목적으로 MFC ActiveX 컨트롤을 자동화 서버로 개발할 수 있습니다. 이러한 컨트롤은 여전히 ActiveX 컨트롤 컨테이너에서 호스팅될 수 있습니다.

### <a name="to-create-a-control-as-an-automation-server"></a>컨트롤을 자동화 서버로 만들려면

1. 컨트롤을 [만듭니다](reference/mfc-activex-control-wizard.md) .

1. [메서드를 추가](mfc-activex-controls-methods.md)합니다.

1. [IsInvokeAllowed](reference/colecontrol-class.md#isinvokeallowed)를 재정의 합니다.

1. 컨트롤을 빌드합니다.

### <a name="to-programmatically-access-the-methods-in-an-automation-server"></a>자동화 서버의 메서드에 프로그래밍 방식으로 액세스 하려면

1. [MFC exe](reference/mfc-application-wizard.md)와 같은 응용 프로그램을 만듭니다.

1. 함수 시작 부분에 `InitInstance` 다음 줄을 추가 합니다.

   [!code-cpp[NVC_MFC_AxCont#17](codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_1.cpp)]

1. 클래스 뷰에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **typelib에서 클래스 추가** 를 선택 하 여 형식 라이브러리를 가져옵니다.

   이렇게 하면 파일 이름 확장명이 .h이 고 .cpp 인 파일이 프로젝트에 추가 됩니다.

1. ActiveX 컨트롤에서 하나 이상의 메서드를 호출 하는 클래스의 헤더 파일에서 다음 줄을 추가 합니다. `#include filename.h` 여기서 file name은 형식 라이브러리를 가져올 때 만들어진 헤더 파일의 이름입니다.

1. ActiveX 컨트롤의 메서드를 호출 하는 함수에서 컨트롤의 래퍼 클래스의 개체를 만들고 ActiveX 개체를 만드는 코드를 추가 합니다. 예를 들어 다음 MFC 코드는 컨트롤을 인스턴스화하고 `CCirc` Caption 속성을 가져오며 대화 상자에서 확인 단추를 클릭 하면 결과를 표시 합니다.

   [!code-cpp[NVC_MFC_AxCont#18](codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_2.cpp)]

응용 프로그램에서 메서드를 사용한 후 ActiveX 컨트롤에 메서드를 추가 하는 경우 형식 라이브러리를 가져올 때 만들어진 파일을 삭제 하 여 응용 프로그램에서 최신 버전의 컨트롤을 사용할 수 있습니다. 그런 다음 형식 라이브러리를 다시 가져옵니다.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)
