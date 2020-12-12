---
description: '자세한 정보: CWinApp 및 MFC 응용 프로그램 마법사'
title: CWinApp 및 MFC 애플리케이션 마법사
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
ms.openlocfilehash: 1ce1f0a84aa5a0f123f9fa8654d1ce286c47d1d9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309266"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp 및 MFC 애플리케이션 마법사

기본 응용 프로그램을 만들 때 MFC 응용 프로그램 마법사는 [CWinApp](reference/cwinapp-class.md)에서 파생 된 응용 프로그램 클래스를 선언 합니다. 또한 MFC 응용 프로그램 마법사는 다음 항목을 포함 하는 구현 파일을 생성 합니다.

- 응용 프로그램 클래스에 대 한 메시지 맵입니다.

- 빈 클래스 생성자입니다.

- 클래스의 한 개체와 유일한 개체를 선언 하는 변수입니다.

- `InitInstance`멤버 함수의 표준 구현입니다.

응용 프로그램 클래스는 프로젝트 헤더 및 주 소스 파일에 배치 됩니다. 만든 클래스 및 파일의 이름은 MFC 응용 프로그램 마법사에서 제공 하는 프로젝트 이름을 기반으로 합니다. 이러한 클래스에 대 한 코드를 보는 가장 쉬운 방법은 [클래스 뷰](/visualstudio/ide/viewing-the-structure-of-code)를 통하는 것입니다.

제공 되는 표준 구현 및 메시지 맵은 많은 용도에 적합 하지만 필요에 따라 수정할 수 있습니다. 이러한 구현의 가장 흥미로운 부분은 `InitInstance` 멤버 함수입니다. 일반적으로의 기초 구현에 코드를 추가 `InitInstance` 합니다.

## <a name="see-also"></a>참고 항목

[CWinApp: 응용 프로그램 클래스](cwinapp-the-application-class.md)<br/>
[재정의 가능 CWinApp 멤버 함수](overridable-cwinapp-member-functions.md)<br/>
[특수 CWinApp 서비스](special-cwinapp-services.md)
