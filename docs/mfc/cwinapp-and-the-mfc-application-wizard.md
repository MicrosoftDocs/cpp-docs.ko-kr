---
title: CWinApp 및 MFC 응용 프로그램 마법사 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWinApp
dev_langs:
- C++
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 009126061856d1165e5d08f6ecc4bd2e7745f2fd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382962"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp 및 MFC 응용 프로그램 마법사

MFC 응용 프로그램 마법사에 응용 프로그램 클래스에서 파생 된 선언 기초 응용 프로그램을 만들 때 [CWinApp](../mfc/reference/cwinapp-class.md)합니다. MFC 응용 프로그램 마법사에는 다음 항목을 포함 하는 구현 파일을 생성 합니다.

- 응용 프로그램 클래스에 대 한 메시지 맵입니다.

- 빈 클래스 생성자입니다.

- 클래스의 개체에 선언 하는 변수입니다.

- 표준 구현에 `InitInstance` 멤버 함수입니다.

응용 프로그램 클래스는 주 소스 파일과 프로젝트 헤더에 배치 됩니다. 클래스 및 생성 된 파일의 이름은 MFC 응용 프로그램 마법사에서 제공한 프로젝트 이름을 기반으로 합니다. 이러한 클래스에 대 한 코드를 볼 수는 가장 쉬운 방법은 방법은 [클래스 뷰](/visualstudio/ide/viewing-the-structure-of-code)합니다.

다양 한 용도로 제공 되는 메시지 맵을 확인 하 고 표준 구현 적합 하지만 필요에 따라 수정할 수 있습니다. 이러한 구현은 가장 흥미로 워 보이지는 `InitInstance` 멤버 함수입니다. 코드를 추가 하는 기본 구현에는 일반적으로 `InitInstance`입니다.

## <a name="see-also"></a>참고 항목

[CWinApp: 응용 프로그램 클래스](../mfc/cwinapp-the-application-class.md)<br/>
[재정의 가능 CWinApp 멤버 함수](../mfc/overridable-cwinapp-member-functions.md)<br/>
[특수 CWinApp 서비스](../mfc/special-cwinapp-services.md)

