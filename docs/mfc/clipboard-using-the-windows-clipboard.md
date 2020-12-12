---
description: '자세히 알아보기: 클립보드: Windows 클립보드 사용'
title: '클립보드: Windows 클립보드 사용'
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard commands
- Cut/Copy and Paste command handler functions [MFC]
- handler functions, Cut/Copy and Paste commands
- Clipboard [MFC], commands
- commands [MFC], implementing Edit
- Clipboard commands [MFC], implementing
- Windows Clipboard [MFC]
- Clipboard [MFC], Windows Clipboard API
ms.assetid: 24415b42-9301-4a70-b69a-44c97918319f
ms.openlocfilehash: 1c89c8888f7e3ffb81705ee146c00917a7763323
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338419"
---
# <a name="clipboard-using-the-windows-clipboard"></a>클립보드: Windows 클립보드 사용

이 항목에서는 MFC 응용 프로그램 내에서 표준 Windows 클립보드 API를 사용 하는 방법에 대해 설명 합니다.

대부분의 Windows 응용 프로그램은 데이터를 Windows 클립보드로 잘라내거나 복사 하 고 클립보드에서 데이터를 붙여 넣는 기능을 지원 합니다. 클립보드 데이터 형식은 응용 프로그램 마다 다릅니다. 프레임 워크는 제한 된 수의 클래스에 대 한 제한 된 수의 클립보드 형식만 지원 합니다. 일반적으로 보기의 편집 메뉴에서 잘라내기, 복사 및 붙여넣기 등의 클립보드 관련 명령을 구현 합니다. 클래스 라이브러리는 **ID_EDIT_CUT**, **ID_EDIT_COPY** 및 **ID_EDIT_PASTE** 명령에 대 한 명령 id를 정의 합니다. 메시지 줄 메시지도 정의 됩니다.

[프레임 워크의 메시지 및 명령은](messages-and-commands-in-the-framework.md) 메뉴 명령을 처리기 함수에 매핑하여 응용 프로그램에서 메뉴 명령을 처리 하는 방법을 설명 합니다. 응용 프로그램에서 편집 메뉴의 클립보드 명령에 대 한 처리기 함수를 정의 하지 않으면 사용 하지 않도록 설정 된 상태로 유지 됩니다. 잘라내기 및 복사 명령에 대 한 처리기 함수를 작성 하려면 응용 프로그램에서 선택 항목을 구현 합니다. 붙여넣기 명령에 대 한 처리기 함수를 작성 하려면 클립보드를 쿼리하여 응용 프로그램이 허용할 수 있는 형식의 데이터가 포함 되어 있는지 확인 합니다. 예를 들어 복사 명령을 사용 하도록 설정 하려면 다음과 같은 처리기를 작성할 수 있습니다.

[!code-cpp[NVC_MFCListView#2](../atl/reference/codesnippet/cpp/clipboard-using-the-windows-clipboard_1.cpp)]

잘라내기, 복사 및 붙여넣기 명령은 특정 컨텍스트에서만 의미가 있습니다. 잘라내기 및 복사 명령은 항목이 선택 된 경우에만 사용 하도록 설정 해야 하 고, 클립보드에 있는 항목은 붙여넣기 명령을 사용 하도록 설정 해야 합니다. 컨텍스트에 따라 이러한 명령을 사용 하거나 사용 하지 않도록 설정 하는 업데이트 처리기 함수를 정의 하 여이 동작을 제공할 수 있습니다. 자세한 내용은 [User-Interface 개체를 업데이트 하는 방법](how-to-update-user-interface-objects.md)을 참조 하세요.

MFC 라이브러리는 및 클래스를 사용 하 여 텍스트를 편집 하기 위한 클립보드 지원을 제공 합니다 `CEdit` `CEditView` . OLE 클래스는 OLE 항목을 포함 하는 클립보드 작업의 구현도 단순화 합니다. OLE 클래스에 대 한 자세한 내용은 [클립보드: Ole 클립보드 메커니즘 사용](clipboard-using-the-ole-clipboard-mechanism.md)을 참조 하세요.

실행 취소 (**ID_EDIT_UNDO**) 및 다시 실행 (**ID_EDIT_REDO**)과 같은 다른 편집 메뉴 명령을 구현 하는 작업도 사용자에 게 남아 있습니다. 응용 프로그램에서 이러한 명령을 지원 하지 않는 경우 Visual C++ 리소스 편집기를 사용 하 여 리소스 파일에서 쉽게 삭제할 수 있습니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [데이터 복사 및 붙여넣기](clipboard-copying-and-pasting-data.md)

- [OLE 클립보드 메커니즘 사용](clipboard-using-the-ole-clipboard-mechanism.md)

## <a name="see-also"></a>참고 항목

[클립보드](clipboard.md)
