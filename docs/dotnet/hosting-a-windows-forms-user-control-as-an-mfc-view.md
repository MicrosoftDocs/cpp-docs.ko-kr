---
description: '자세한 정보: Windows Forms 사용자 정의 컨트롤을 MFC 뷰로 호스팅'
title: Windows Forms 사용자 정의 컨트롤을 MFC 뷰로 호스팅
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms controls [C++], hosting as an MFC view
- hosting Windows Forms control [C++]
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
ms.openlocfilehash: 4e66d4ace83e0026ec7a95cbe1b94462a163dddf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164642"
---
# <a name="hosting-a-windows-forms-user-control-as-an-mfc-view"></a>Windows Forms 사용자 정의 컨트롤을 MFC 뷰로 호스팅

MFC는 CWinFormsView 클래스를 사용 하 여 MFC 뷰에서 Windows Forms 사용자 정의 컨트롤을 호스팅합니다. MFC Windows Forms 뷰는 ActiveX 컨트롤입니다. 사용자 정의 컨트롤은 네이티브 뷰의 자식으로 호스팅되고 네이티브 뷰의 전체 클라이언트 영역을 차지 합니다.

최종 결과는 [CFormView 클래스](../mfc/reference/cformview-class.md)에서 사용 하는 모델과 유사 합니다. 이렇게 하면 Windows Forms 디자이너와 런타임을 활용 하 여 풍부한 폼 기반 보기를 만들 수 있습니다.

MFC Windows Forms 뷰는 ActiveX 컨트롤 이므로 MFC 뷰와 동일 하지 않습니다 `hwnd` . 또한 [CView](../mfc/reference/cview-class.md) 뷰에서 포인터로 전달할 수 없습니다. 일반적으로 .NET Framework 메서드를 사용 하 여 Windows Forms 보기로 작업 하 고 Win32에서 사용 하는 것이 더 낮습니다.

MFC와 함께 사용 Windows Forms을 보여 주는 예제 응용 프로그램은 [mfc 및 Windows Forms 통합](https://www.microsoft.com/download/details.aspx?id=2113)을 참조 하세요.

## <a name="in-this-section"></a>섹션 내용

[방법: 사용자 정의 컨트롤 및 호스트 MDI 뷰 만들기](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)

[방법: Windows Forms 컨트롤에 명령 라우팅 추가](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)

[방법: Windows Forms 컨트롤의 속성 및 메서드 호출](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)

## <a name="see-also"></a>참고 항목

[MFC에서 Windows Form 사용자 정의 컨트롤 사용](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[방법: 복합 컨트롤 작성](/dotnet/framework/winforms/controls/how-to-author-composite-controls)
