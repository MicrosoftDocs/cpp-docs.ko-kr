---
description: '자세한 정보: OLE의 대화 상자'
title: OLE의 대화 상자
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], OLE dialog boxes
- OLE dialog boxes
- dialog boxes
- OLE dialog boxes [MFC], about OLE dialog boxes
- dialog boxes [MFC], about dialog boxes
- dialog boxes [MFC], OLE
- Insert object
ms.assetid: 73c41eb8-738a-4d02-9212-d3395bb09a3a
ms.openlocfilehash: 39353e75fafd65af1f3e5665afce28e3495a978b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261504"
---
# <a name="dialog-boxes-in-ole"></a>OLE의 대화 상자

사용자가 OLE 사용 응용 프로그램을 실행 하는 동안 작업을 수행 하기 위해 응용 프로그램에 사용자의 정보가 필요할 수 있습니다. MFC OLE 클래스는 필요한 정보를 수집할 수 있는 여러 대화 상자를 제공 합니다. 이 항목에서는 OLE 대화 상자에서 처리 되는 작업과 해당 대화 상자를 표시 하는 데 필요한 클래스를 나열 합니다. OLE 대화 상자와 해당 동작을 사용자 지정 하는 데 사용 되는 구조에 대 한 자세한 내용은 [MFC 참조](mfc-desktop-applications.md)를 참조 하세요.

*개체 삽입*<br/>
이 대화 상자에서는 사용자가 새로 만들었거나 기존 개체를 복합 문서에 삽입할 수 있습니다. 또한 사용자가 항목을 아이콘으로 표시 하도록 선택 하 고 아이콘 변경 명령 단추를 사용 하도록 설정할 수 있습니다. 사용자가 편집 메뉴에서 개체 삽입을 선택 하면이 대화 상자가 표시 됩니다. [Coleinsertdialog](reference/coleinsertdialog-class.md) 클래스를 사용 하 여이 대화 상자를 표시할 수 있습니다. MDI 응용 프로그램은 자체에 삽입할 수 없습니다. 컨테이너/서버 응용 프로그램은 SDI 응용 프로그램이 아닌 경우 자체에 삽입할 수 없습니다.

*선택하여 붙여넣기*<br/>
사용자는이 대화 상자를 사용 하 여 데이터를 복합 문서에 붙여넣을 때 사용 되는 형식을 제어할 수 있습니다. 사용자는 데이터의 형식을 선택 하 고, 데이터를 포함할지 아니면 연결할지를 선택 하 고, 데이터를 아이콘으로 표시할지 여부를 선택할 수 있습니다. 사용자가 편집 메뉴에서 선택 하 여 붙여넣기를 선택 하면이 대화 상자가 표시 됩니다. [COlePasteSpecialDialog](reference/colepastespecialdialog-class.md) 클래스를 사용 하 여이 대화 상자를 표시 합니다.

*아이콘 변경*<br/>
이 대화 상자를 통해 사용자는 연결 된 항목 또는 포함 된 항목을 나타내기 위해 표시 되는 아이콘을 선택할 수 있습니다. 사용자가 편집 메뉴에서 변경 아이콘을 선택 하거나 붙여넣기 특수 또는 변환 대화 상자에서 아이콘 변경 단추를 선택 하면이 대화 상자를 표시 합니다. 사용자가 개체 삽입 대화 상자를 열고 아이콘으로 표시를 선택 하는 경우에도 표시 합니다. [COleChangeIconDialog](reference/colechangeicondialog-class.md) 클래스를 사용 하 여이 대화 상자를 표시 합니다.

*변환*<br/>
이 대화 상자를 사용 하 여 포함 되거나 연결 된 항목의 형식을 변경할 수 있습니다. 예를 들어 복합 문서에 메타 파일을 포함 하 고 나중에 다른 응용 프로그램을 사용 하 여 포함 된 메타 파일을 수정 하려는 경우 변환 대화 상자를 사용할 수 있습니다. 이 대화 상자는 일반적으로 편집 메뉴에서 *항목 유형* 개체를 클릭 한 다음 계단식 메뉴에서 변환을 클릭 하 여 표시 됩니다. [COleConvertDialog](reference/coleconvertdialog-class.md) 클래스를 사용 하 여이 대화 상자를 표시 합니다. 예제를 보려면 MFC OLE 샘플 [OCLIENT](../overview/visual-cpp-samples.md)를 실행 합니다.

*링크 편집 또는 링크 업데이트*<br/>
링크 편집 대화 상자를 사용 하 여 사용자는 연결 된 개체의 원본에 대 한 정보를 변경할 수 있습니다. 업데이트 링크 대화 상자는 현재 대화 상자에 있는 모든 연결 된 항목의 원본을 확인 하 고 필요한 경우 링크 편집 대화 상자를 표시 합니다. 사용자가 편집 메뉴에서 링크를 선택할 때 링크 편집 대화 상자를 표시 합니다. 업데이트 링크 대화 상자는 일반적으로 복합 문서를 처음 열 때 표시 됩니다. 표시 하려는 대화 상자에 따라 [COleLinksDialog](reference/colelinksdialog-class.md) 또는 [coleupdatedialog](reference/coleupdatedialog-class.md) 클래스 중 하나를 사용 합니다.

*서버 작업 중 또는 서버가 응답 하지 않음*<br/>
서버 작업 중 대화 상자는 사용자가 항목을 활성화 하려고 할 때 서버에서 현재 요청을 처리할 수 없는 경우 (일반적으로 다른 사용자 또는 작업에서 서버를 사용 하 고 있기 때문에) 표시 됩니다. 서버가 활성화 요청에 응답 하지 않으면 서버가 응답 하지 않습니다. 대화 상자가 표시 됩니다. 이러한 대화 상자는 `COleMessageFilter` OLE 인터페이스의 구현에 따라를 통해 표시 되며, `IMessageFilter` 사용자는 활성화 요청을 다시 시도할지 여부를 결정할 수 있습니다. [COleBusyDialog](reference/colebusydialog-class.md) 클래스를 사용 하 여이 대화 상자를 표시 합니다.

## <a name="see-also"></a>참고 항목

[대화 상자](dialog-boxes.md)<br/>
[MFC에서 대화 상자를 통해 작업](life-cycle-of-a-dialog-box.md)<br/>
[OLE](ole-in-mfc.md)
