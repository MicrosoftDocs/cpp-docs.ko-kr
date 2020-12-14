---
description: '자세히 알아보기: MFC 대화 상자에서 Windows Form 사용자 정의 컨트롤 호스팅'
title: MFC 대화 상자에서 Windows Form 사용자 정의 컨트롤 호스팅
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 3ccfbb32132f5732c244473c652bb6b2df175efa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335445"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>MFC 대화 상자에서 Windows Form 사용자 정의 컨트롤 호스팅

MFC는 Windows Forms 컨트롤을 특수 한 종류의 ActiveX 컨트롤로 호스팅하고 ActiveX 인터페이스, 클래스의 속성 및 메서드를 사용 하 여 컨트롤과 통신 <xref:System.Windows.Forms.Control> 합니다. .NET Framework 속성 및 메서드를 사용 하 여 컨트롤에서 작동 하는 것이 좋습니다.

MFC와 함께 사용 Windows Forms을 보여 주는 예제 응용 프로그램은 [mfc 및 Windows Forms 통합](https://www.microsoft.com/download/details.aspx?id=2113)을 참조 하세요.

> [!NOTE]
> 현재 릴리스에서 `CDialogBar` 개체는 Windows Forms 컨트롤을 호스트할 수 없습니다.

## <a name="in-this-section"></a>섹션 내용

[방법: 대화 상자에 사용자 정의 컨트롤 및 호스트 만들기](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[방법: Windows Forms를 사용 하 여 DDX/DDV 데이터 바인딩 수행](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[방법: 네이티브 c + + 클래스에서 Windows Forms 이벤트 싱크](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>참조

[CWinFormsControl 클래스](../mfc/reference/cwinformscontrol-class.md) &#124; [CDialog](../mfc/reference/cdialog-class.md) 클래스 &#124; [CWnd 클래스](../mfc/reference/cwnd-class.md) &#124; <xref:System.Windows.Forms.Control>

## <a name="see-also"></a>참고 항목

[MFC에서 Windows Form 사용자 정의 컨트롤 사용](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Windows Forms/MFC 프로그래밍 차이점](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[Windows Forms 사용자 정의 컨트롤을 MFC 뷰로 호스팅](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Windows Form 사용자 정의 컨트롤을 MFC 대화 상자로 호스팅](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
