---
description: '자세히 알아보기: MFC에서 Windows Form 사용자 정의 컨트롤 사용'
title: MFC에서 Windows Form 사용자 정의 컨트롤 사용
ms.date: 01/08/2018
helpviewer_keywords:
- MFC [C++], Windows Forms support
- interoperability [C++], Windows Forms in MFC
- interoperability [C++], MFC
- interop [C++], Windows Forms in MFC
- interop [C++], MFC
- Windows Forms [C++], MFC support
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
ms.openlocfilehash: 61022d241faba1650d1a044ef6d3667febe34cde
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319029"
---
# <a name="using-a-windows-form-user-control-in-mfc"></a>MFC에서 Windows Form 사용자 정의 컨트롤 사용

Mfc Windows Forms 지원 클래스를 사용 하 여 mfc 대화 상자 또는 뷰에서 ActiveX 컨트롤로 MFC 응용 프로그램 내에서 Windows Forms 컨트롤을 호스트할 수 있습니다. 또한 Windows Forms Forms는 MFC 대화 상자로 호스팅될 수 있습니다.

다음 섹션에서는 다음을 수행 하는 방법을 설명 합니다.

- MFC 대화 상자에서 Windows Forms 컨트롤을 호스팅합니다.

- Windows Forms 사용자 정의 컨트롤을 MFC 뷰로 호스팅합니다.

- Windows Forms 폼을 MFC 대화 상자로 호스팅합니다.

> [!NOTE]
> MFC Windows Forms 통합은 MFC (가 정의 된 프로젝트)와 동적으로 연결 되는 프로젝트 에서만 작동 `_AFXDLL` 합니다.

> [!NOTE]
> MFC Windows Forms 인터페이스 DLL (mfcmifc80.dll)의 전용 (수정 됨) 복사본을 사용 하 여 응용 프로그램을 빌드할 때 Microsoft 키를 고유한 공급 업체 키로 대체 하지 않으면 GAC에 설치 되지 않습니다. 어셈블리 서명에 대 한 자세한 내용은 어셈블리를 [사용한 프로그래밍](/dotnet/framework/app-domains/programming-with-assemblies) 및 [강력한 이름 어셈블리 (어셈블리 서명) (c + +/cli)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)를 참조 하세요.

MFC 응용 프로그램에서 Windows Forms 사용 하는 경우 응용 프로그램과 mfcmifc80.dll를 재배포 해야 합니다. 자세한 내용은 [MFC 라이브러리 재배포](../windows/redistributing-the-mfc-library.md)를 참조 하세요.

## <a name="in-this-section"></a>섹션 내용

[MFC 대화 상자에서 Windows Form 사용자 정의 컨트롤 호스팅](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)

[Windows Forms 사용자 정의 컨트롤을 MFC 뷰로 호스팅](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)

[Windows Form 사용자 정의 컨트롤을 MFC 대화 상자로 호스팅](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)

## <a name="reference"></a>참조

[CWinFormsControl 클래스](../mfc/reference/cwinformscontrol-class.md)

[CWinFormsDialog 클래스](../mfc/reference/cwinformsdialog-class.md)

[CWinFormsView 클래스](../mfc/reference/cwinformsview-class.md)

[ICommandSource 인터페이스](../mfc/reference/icommandsource-interface.md)

[ICommandTarget 인터페이스](../mfc/reference/icommandtarget-interface.md)

[ICommandUI 인터페이스](../mfc/reference/icommandui-interface.md)

[IView 인터페이스](../mfc/reference/iview-interface.md)

[CommandHandler](../atl/commandhandler.md)

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)

[UICheckState](../mfc/reference/uicheckstate-enumeration.md)

## <a name="related-sections"></a>관련 단원

[Windows Forms](/dotnet/framework/winforms/index)

[Windows Forms 컨트롤](/dotnet/framework/winforms/controls/index)

## <a name="see-also"></a>참고 항목

[사용자 인터페이스 요소](../mfc/user-interface-elements-mfc.md)<br/>
[폼 뷰](../mfc/form-views-mfc.md)
