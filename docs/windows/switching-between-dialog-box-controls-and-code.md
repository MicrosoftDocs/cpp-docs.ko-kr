---
title: 대화 상자 (c + +) 컨트롤과 코드 사이의 전환
ms.date: 11/04/2016
helpviewer_keywords:
- events [C++], viewing for controls
- Windows messages [C++], controls
- messages [C++], viewing for dialog boxes
- Dialog Editor [C++], accessing code
- code [C++], switching from Dialog Editor
- controls [C++], jumping to code
- Dialog Editor [C++], switching between controls and code
ms.assetid: 7da73815-b853-4203-ba45-bbe570695122
ms.openlocfilehash: 4d48386e93fcea6d30fee6c57c288944bbd8d9ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644303"
---
# <a name="switching-between-dialog-box-c-controls-and-code"></a>대화 상자 (c + +) 컨트롤과 코드 사이의 전환

MFC 응용 프로그램에서 대화 상자 컨트롤 처리기 코드로 이동할 또는 신속 하 게 만들 스텁 처리기 함수에 두 번 클릭 수 있습니다.

선택한 컨트롤을 클릭 합니다 **컨트롤 이벤트** 단추 또는 **메시지** 단추를 [속성 창](/visualstudio/ide/reference/properties-window) Windows 메시지 및 이벤트의 전체 목록을 보려면 선택한 항목에 대해 사용할 수 있습니다. 목록에서 만들기 또는 편집 처리기 함수를 선택 합니다.

### <a name="to-jump-to-code-from-the-dialog-editor"></a>대화 상자 편집기에서 코드로 이동할 수

1. 가장 최근에 구현된 해당 메시지 처리 기능에 대 한 선언으로 이동 대화 상자 내에 있는 컨트롤을 두 번 클릭 합니다. (ATL 기반 대화 상자 클래스에 대해 항상 이동할 있습니다 생성자 정의 합니다.)

### <a name="to-view-events-for-a-control"></a>컨트롤에 대 한 이벤트를 보려면

1. 선택한 컨트롤을 클릭 합니다 **컨트롤 이벤트** 단추를 [속성 창](/visualstudio/ide/reference/properties-window)합니다.

   > [!NOTE]
   > 클릭 하는 **컨트롤 이벤트** 표시 되 면 합니다 *대화 상자* 에 포커스 노출 목록이 있는 모든 컨트롤의 개별 컨트롤에 대 한 이벤트를 편집 하려면 다음 확장할 수 있는 대화 상자에서.

   마우스 오른쪽 단추로 클릭 하 고 선택할 수, 단일 컨트롤을 대화 상자에 포커스가 있으면 **이벤트 처리기 추가** 바로 가기 메뉴에서. 이 처리기가 추가 되는 클래스를 지정할 수 있습니다. 자세한 내용은 [이벤트 처리기를 추가](../ide/adding-an-event-handler-visual-cpp.md)합니다.

### <a name="to-view-messages-for-a-dialog-box"></a>대화 상자에 대 한 메시지를 보려면

1. 선택 대화 상자를 클릭 합니다 **메시지** 단추를 [속성 창](/visualstudio/ide/reference/properties-window)합니다.

관리 되는 프로젝트에 리소스를 추가 하는 방법에 대 한 정보를 참조 하세요 [데스크톱 앱의 리소스](/dotnet/framework/resources/index) 에 *.NET Framework Developer's Guide*합니다. 수동으로 관리 되는 프로젝트에 리소스 파일을 추가, 리소스 액세스, 정적 리소스 표시 및 속성에 리소스 문자열 할당에 대 한 내용은 참조 하세요 [데스크톱 앱에 대 한 리소스 파일 만들기](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)합니다. 전역화 및 지역화 관리 되는 앱의 리소스에 대 한 내용은 참조 하세요 [Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)합니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[대화 상자 편집기](../windows/dialog-editor.md)