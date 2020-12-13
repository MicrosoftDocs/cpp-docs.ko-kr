---
description: '자세한 정보: MFC 응용 프로그램 마법사에서 만든 문서 및 뷰 클래스'
title: MFC 애플리케이션 마법사에서 만든 문서 및 뷰 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- document classes [MFC]
- document classes [MFC], created by application wizards
- application wizards [MFC], document/view classes created
- view classes [MFC], created by application wizards
ms.assetid: 70c34a60-2701-4981-acea-c08a5787d8e6
ms.openlocfilehash: f182278ebdd971364e3e35e15e51b6ea5e7aaf68
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330319"
---
# <a name="document-and-view-classes-created-by-the-mfc-application-wizard"></a>MFC 애플리케이션 마법사에서 만든 문서 및 뷰 클래스

MFC 응용 프로그램 마법사를 사용 하면 기초 문서와 뷰 클래스를 만들어 프로그램 개발을 시작할 수 있습니다. 그런 다음 [이러한 클래스에 명령 및 메시지를 매핑하고](reference/mapping-messages-to-functions.md) Visual C++ 소스 코드 편집기를 사용 하 여 해당 멤버 함수를 작성할 수 있습니다.

MFC 응용 프로그램 마법사에서 만든 문서 클래스는 [CDocument](reference/cdocument-class.md)클래스에서 파생 됩니다. 뷰 클래스는 [CView](reference/cview-class.md)에서 파생 됩니다. 응용 프로그램 마법사가 이러한 클래스와 이러한 클래스를 포함 하는 파일을 제공 하는 이름은 응용 프로그램 마법사 대화 상자에서 제공 하는 프로젝트 이름을 기반으로 합니다. 응용 프로그램 마법사에서 생성 된 클래스 페이지를 사용 하 여 기본 이름을 변경할 수 있습니다.

일부 응용 프로그램에는 둘 이상의 문서 클래스, 뷰 클래스 또는 프레임 창 클래스가 필요할 수 있습니다. 자세한 내용은 [여러 문서 형식, 뷰 및 프레임 창](multiple-document-types-views-and-frame-windows.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[문서/뷰 아키텍처](document-view-architecture.md)
