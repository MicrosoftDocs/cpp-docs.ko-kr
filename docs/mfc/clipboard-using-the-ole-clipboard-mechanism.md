---
description: '자세히 알아보기: 클립보드: OLE 클립보드 메커니즘 사용'
title: '클립보드: OLE 클립보드 메커니즘 사용'
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], Clipboard
- OLE Clipboard
- Clipboard [MFC], OLE formats
- OLE Clipboard, formats
- formats [MFC], Clipboard for OLE
ms.assetid: 229cc610-5bb1-435e-bd20-2c8b9964d1af
ms.openlocfilehash: f7005bd3e99ebb658b6aa38952a6689d4a9ba30c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338437"
---
# <a name="clipboard-using-the-ole-clipboard-mechanism"></a>클립보드: OLE 클립보드 메커니즘 사용

OLE는 클립보드를 통해 데이터를 전송 하기 위해 표준 형식 및 일부 OLE 관련 형식을 사용 합니다.

응용 프로그램에서 데이터를 잘라내거나 복사할 때 데이터는 나중에 붙여넣기 작업에서 사용 하기 위해 클립보드에 저장 됩니다. 이 데이터는 다양 한 형식입니다. 사용자가 클립보드에서 데이터를 붙여 넣을 때 응용 프로그램에서 사용할 형식을 선택할 수 있습니다. 사용자가 특별히 붙여넣기를 사용 하 여 특정 형식을 요구 하지 않는 한 가장 많은 정보를 제공 하는 형식을 선택 하도록 응용 프로그램을 작성 해야 합니다. 계속 하기 전에 [데이터 개체 및 데이터 소스 (OLE)](data-objects-and-data-sources-ole.md) 항목을 읽어야 할 수 있습니다. 이러한 작업은 데이터 전송의 기본 사항과 응용 프로그램에서이를 구현 하는 방법에 대 한 기본 사항을 설명 합니다.

Windows는 클립보드를 통해 데이터를 전송 하는 데 사용할 수 있는 여러 표준 형식을 정의 합니다. 여기에는 메타 파일, 텍스트, 비트맵 등이 포함 됩니다. OLE는 다양 한 OLE 관련 형식도 정의 합니다. 이러한 표준 형식에 지정 된 것 보다 더 자세한 정보를 필요로 하는 응용 프로그램의 경우 고유한 사용자 지정 클립보드 형식을 등록 하는 것이 좋습니다. 이 작업을 수행 하려면 Win32 API 함수 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 를 사용 합니다.

예를 들어 Microsoft Excel은 스프레드시트의 사용자 지정 형식을 등록 합니다. 예를 들어이 형식은 비트맵 처럼 훨씬 더 많은 정보를 전달 합니다. 스프레드시트 형식을 지 원하는 응용 프로그램에이 데이터를 붙여넣으면 스프레드시트의 모든 수식과 값이 유지 되며 필요한 경우 업데이트할 수 있습니다. 또한 Microsoft Excel은 클립보드의 데이터를 OLE 항목으로 붙여 넣을 수 있도록 형식으로 저장 합니다. OLE 문서 컨테이너는이 정보를 포함 된 항목으로 붙여 넣을 수 있습니다. Microsoft Excel을 사용 하 여 포함 된 항목을 변경할 수 있습니다. 클립보드에는 스프레드시트에서 선택한 범위의 이미지에 대 한 간단한 비트맵만 포함 됩니다. 이를 OLE 문서 컨테이너 또는 그리기와 같은 비트맵 편집기에 붙여 넣을 수도 있습니다. 그러나 비트맵의 경우 데이터를 스프레드시트로 조작할 수 있는 방법이 없습니다.

클립보드에서 데이터의 최대 크기를 검색 하기 위해 응용 프로그램은 클립보드에서 데이터를 붙여 넣기 전에 이러한 사용자 지정 형식을 확인 해야 합니다.

예를 들어 Cut 명령을 사용 하도록 설정 하려면 다음과 같은 처리기를 작성할 수 있습니다.

[!code-cpp[NVC_MFCListView#3](../atl/reference/codesnippet/cpp/clipboard-using-the-ole-clipboard-mechanism_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [데이터 복사 및 붙여넣기](clipboard-copying-and-pasting-data.md)

- [다른 형식 추가](clipboard-adding-other-formats.md)

- [Windows 클립보드 사용](clipboard-using-the-windows-clipboard.md)

- [OLE](ole-background.md)

- [OLE 데이터 개체 및 데이터 원본 및 균일 한 데이터 전송](data-objects-and-data-sources-ole.md)

## <a name="see-also"></a>참고 항목

[클립보드](clipboard.md)
