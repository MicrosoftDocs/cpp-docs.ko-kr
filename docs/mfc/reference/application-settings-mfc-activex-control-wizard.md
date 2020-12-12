---
description: '자세히 알아보기: 응용 프로그램 설정, MFC ActiveX 컨트롤 마법사'
title: 애플리케이션 설정, MFC ActiveX 컨트롤 마법사
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.appset
helpviewer_keywords:
- MFC ActiveX Control Wizard, application settings
ms.assetid: 48475194-cc63-467f-8499-f142269a4c1c
ms.openlocfilehash: dac370f7ba3461534f2fd4782869e7ddcb50336a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322813"
---
# <a name="application-settings-mfc-activex-control-wizard"></a>애플리케이션 설정, MFC ActiveX 컨트롤 마법사

MFC ActiveX 컨트롤 마법사의 이 페이지를 사용하여 기본 기능을 디자인하고 새 MFC ActiveX 프로젝트에 추가합니다. 이러한 설정은 컨트롤의 특정 기능이나 요소가 아닌 애플리케이션 자체에 적용됩니다.

- **런타임 라이선스**

   컨트롤과 함께 배포할 사용자 라이선스 파일을 생성하려면 이 옵션을 선택합니다. 라이선스는 텍스트 파일인 *projname*.lic입니다. 디자인 타임 환경에서 컨트롤의 인스턴스를 만들 수 있도록 하려면 이 파일이 컨트롤의 DLL과 같은 디렉터리에 있어야 합니다. 일반적으로 컨트롤과 함께 이 파일을 배포하지만 고객은 배포하지 않습니다.

- **도움말 파일 생성**

   도움말 파일을 생성하고 컨트롤에 대한 도움말을 포함하도록 프로젝트를 구성하려면 이 옵션을 선택합니다. 이 옵션을 사용하지 않고 만든 기본 프로젝트에는 사용자가 컨트롤을 마우스 오른쪽 단추로 클릭하거나, F1 키를 사용하거나, 컨트롤의 컨테이너에서 **도움말** 을 클릭하면 표시되는 **정보** 상자만 생성됩니다.

   > [!NOTE]
   > 도움말 표시 방법은 컨트롤과 컨테이너의 상호 작용 방법에 따라 달라집니다. 컨테이너에 대한 도움말을 포함하는 경우 도움말을 적절히 표시하려면 컨트롤과 컨테이너 간의 메시지를 처리해야 합니다.

   마법사를 사용하여 도움말 파일을 생성하면 프로젝트에 다음 항목이 포함됩니다.

  - .vcxproj 파일에는 프로젝트가 빌드될 때 도움말 파일을 빌드하고 구성하는 코드가 포함됩니다.

  - *projnamePropPage*.cpp 파일은 [SetHelpInfo](../../mfc/reference/colepropertypage-class.md#sethelpinfo) 함수를 생성자에 포함합니다.

  - projname.hpj 파일은 도움말 컴파일러에서 ActiveX 컨트롤의 도움말 파일을 만드는 데 사용되는 도움말 프로젝트 파일입니다. .hpj 파일은 도움말 파일 빌드에 대한 정보 및 도움말 파일에 포함되는 추가 파일(예: 비트맵)에 대한 경로를 포함하는 텍스트 파일입니다.

  - 프로젝트에는 프로젝트 도움말 비트맵 파일 및 도움말 항목 파일(*projname*.rtf)을 포함하는 HLP 디렉터리가 있습니다. 이 도움말 항목 파일에는 많은 ActiveX 컨트롤에서 지원하는 공용 속성, 이벤트 및 메서드에 대한 표준 도움말 항목이 포함됩니다. .rtf 파일을 편집하여 특정 도움말 항목을 추가하거나 제거할 수 있습니다.

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤 마법사](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[MFC ActiveX 컨트롤 마법사, 컨트롤 이름](../../mfc/reference/control-names-mfc-activex-control-wizard.md)<br/>
[MFC ActiveX 컨트롤 마법사, 컨트롤 설정](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)
