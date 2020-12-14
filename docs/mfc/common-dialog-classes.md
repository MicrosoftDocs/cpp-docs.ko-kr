---
description: '자세히 알아보기: 일반 대화 상자 클래스'
title: 일반 대화 상자 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- dialog classes [MFC]
- dialog boxes [MFC], Windows common dialogs
- common dialog boxes [MFC], common dialog classes
- common dialog classes [MFC]
- MFC dialog boxes [MFC], Windows common dialogs
- Windows common dialogs [MFC]
- dialog classes [MFC], common
- common dialog boxes [MFC]
ms.assetid: 5c4f6443-896c-4b05-a7df-8169fdadc71d
ms.openlocfilehash: 8ab72407c9d709ef660976105d65901398ae5b5b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310686"
---
# <a name="common-dialog-classes"></a>일반 대화 상자 클래스

클래스 [CDialog](reference/cdialog-class.md)외에 MFC는 `CDialog` 다음 표와 같이 일반적으로 사용 되는 대화 상자를 캡슐화 하는에서 파생 된 여러 클래스를 제공 합니다. 캡슐화 된 대화 상자를 "일반 대화 상자" 라고 하며,이 대화 상자는 COMMDLG.DLL (Windows 공용 대화 상자 라이브러리)의 일부입니다. 이러한 클래스에 대 한 대화 상자 템플릿 리소스 및 코드는 Windows 버전 3.1 이상에 포함 된 Windows 공용 대화 상자에 제공 됩니다.

### <a name="common-dialog-classes"></a>일반 대화 상자 클래스

|파생 된 대화 상자 클래스|목적|
|--------------------------|-------------|
|[CColorDialog](reference/ccolordialog-class.md)|사용자가 색을 선택할 수 있습니다.|
|[CFileDialog](reference/cfiledialog-class.md)|사용자가 열거나 저장할 파일 이름을 선택할 수 있습니다.|
|[CFindReplaceDialog](reference/cfindreplacedialog-class.md)|사용자가 텍스트 파일에서 찾기 또는 바꾸기 작업을 시작할 수 있습니다.|
|[CFontDialog](reference/cfontdialog-class.md)|사용자가 글꼴을 지정할 수 있습니다.|
|[CPrintDialog](reference/cprintdialog-class.md)|사용자가 인쇄 작업에 대 한 정보를 지정할 수 있습니다.|
|[CPrintDialogEx](reference/cprintdialogex-class.md)|Windows 인쇄 속성 시트입니다.|

일반 대화 상자 클래스에 대 한 자세한 내용은 *MFC 참조* 에서 개별 클래스 이름을 참조 하세요. 또한 MFC는 OLE에 사용 되는 여러 가지 표준 대화 상자 클래스를 제공 합니다. 이러한 클래스에 대 한 자세한 내용은 *MFC 참조* 에서 기본 클래스인 [coledialog](reference/coledialog-class.md)를 참조 하세요.

MFC의 세 가지 다른 클래스에는 대화 상자와 같은 특징이 있습니다. [CFormView](reference/cformview-class.md), [CRecordView](reference/crecordview-class.md)및 [CDaoRecordView](reference/cdaorecordview-class.md)클래스에 대 한 자세한 내용은 *MFC 참조* 의 클래스를 참조 하세요. [CDialogBar](reference/cdialogbar-class.md)클래스에 대 한 자세한 내용은 [대화 상자 모음](dialog-bars.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[대화 상자](dialog-boxes.md)<br/>
[MFC에서 대화 상자를 통해 작업](life-cycle-of-a-dialog-box.md)<br/>
[OLE의 대화 상자](dialog-boxes-in-ole.md)
