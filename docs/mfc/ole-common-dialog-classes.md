---
description: '자세한 정보: OLE 일반 대화 상자 클래스'
title: OLE 일반 대화 상자 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- dialog classes [MFC], OLE
- OLE common dialog classes [MFC]
- common dialog classes [MFC]
ms.assetid: 706526ae-f94f-4909-a0f8-6b5fe954fd97
ms.openlocfilehash: c30871c8f49be608f5ceeea3d84c86d483e20a81
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222283"
---
# <a name="ole-common-dialog-classes"></a>OLE 일반 대화 상자 클래스

이러한 클래스는 다양 한 표준 OLE 대화 상자를 구현 하 여 일반적인 OLE 태스크를 처리 합니다. 또한 OLE 기능에 대해 일관 된 사용자 인터페이스를 제공 합니다.

[COleDialog](reference/coledialog-class.md)<br/>
프레임 워크에서 모든 OLE 대화 상자에 대 한 일반적인 구현을 포함 하는 데 사용 됩니다. 사용자 인터페이스 범주의 모든 대화 상자 클래스는이 기본 클래스에서 파생 됩니다. `COleDialog` 직접 사용할 수 없습니다.

[COleInsertDialog](reference/coleinsertdialog-class.md)<br/>
새 OLE 연결 된 항목 또는 포함 된 항목을 삽입 하기 위한 표준 사용자 인터페이스인 개체 삽입 대화 상자를 표시 합니다.

[COlePasteSpecialDialog](reference/colepastespecialdialog-class.md)<br/>
붙여넣기 특수 편집 명령을 구현 하기 위한 표준 사용자 인터페이스인 붙여넣기 특수 대화 상자를 표시 합니다.

[COleLinksDialog](reference/colelinksdialog-class.md)<br/>
연결 된 항목에 대 한 정보를 수정 하기 위한 표준 사용자 인터페이스인 링크 편집 대화 상자를 표시 합니다.

[COleChangeIconDialog](reference/colechangeicondialog-class.md)<br/>
OLE 포함 또는 연결 된 항목과 연결 된 아이콘을 변경 하기 위한 표준 사용자 인터페이스인 아이콘 변경 대화 상자를 표시 합니다.

[COleConvertDialog](reference/coleconvertdialog-class.md)<br/>
OLE 항목을 한 형식에서 다른 형식으로 변환 하기 위한 표준 사용자 인터페이스인 변환 대화 상자를 표시 합니다.

[COlePropertiesDialog](reference/colepropertiesdialog-class.md)<br/>
Windows 공용 OLE 속성 대화 상자를 캡슐화 합니다. 일반적인 OLE 속성 대화 상자를 사용 하면 Windows 표준과 일관 된 방식으로 OLE 문서 항목의 속성을 쉽게 표시 하 고 수정할 수 있습니다.

[COleUpdateDialog](reference/coleupdatedialog-class.md)<br/>
문서의 모든 링크를 업데이트 하기 위한 표준 사용자 인터페이스인 업데이트 대화 상자를 표시 합니다. 이 대화 상자에는 업데이트 절차를 완료 하는 방법을 나타내는 진행률 표시기가 있습니다.

[COleChangeSourceDialog](reference/colechangesourcedialog-class.md)<br/>
링크의 대상 또는 소스를 변경 하기 위한 표준 사용자 인터페이스인 소스 변경 대화 상자를 표시 합니다.

[COleBusyDialog](reference/colebusydialog-class.md)<br/>
사용 중인 응용 프로그램에 대 한 호출을 처리 하기 위한 표준 사용자 인터페이스인 서버 사용 중 및 서버 응답 없음 대화 상자를 표시 합니다. 일반적으로 구현에 의해 자동으로 표시 `COleMessageFilter` 됩니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](class-library-overview.md)
