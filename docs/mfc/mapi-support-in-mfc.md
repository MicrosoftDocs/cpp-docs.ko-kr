---
description: '자세히 알아보기: MFC의 MAPI 지원'
title: MFC의 MAPI 지원
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, MAPI support
- MAPI support in MFC
- CDocument class [MFC], and MAPI
- OnUpdateFileSendMail method [MFC]
- MAPI, MFC
- OnFileSendMail method [MFC]
ms.assetid: cafbecb1-0427-4077-b4b8-159bae5b49b8
ms.openlocfilehash: 289ad61894efd5c08d3a50d8c50e3ac6ee518a25
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280757"
---
# <a name="mapi-support-in-mfc"></a>MFC의 MAPI 지원

MFC는 클래스의 Microsoft MAPI (메시징 응용 프로그램 인터페이스)의 하위 집합에 대 한 지원을 제공 `CDocument` 합니다. 특히에는 `CDocument` 메일 지원이 최종 사용자의 컴퓨터에 있는지 여부를 결정 하는 멤버 함수가 있으며,이 경우 표준 명령 ID가 ID_FILE_SEND_MAIL 인 메일 보내기 명령을 사용 하도록 설정 합니다. 이 명령의 MFC 처리기 함수를 사용 하면 사용자가 전자 메일을 통해 문서를 보낼 수 있습니다.

> [!TIP]
> MFC는 전체 MAPI 함수 집합을 캡슐화 하지 않지만 MFC 프로그램에서 직접 Win32 API 함수를 호출 하는 것 처럼 MAPI 함수를 직접 호출할 수 있습니다.

응용 프로그램에서 메일 보내기 명령을 쉽게 제공할 수 있습니다. MFC는 문서 (즉, `CDocument` 파생 개체)를 첨부 파일로 패키지 하 고 메일로 보내도록 구현을 제공 합니다. 이 첨부 파일은 문서 내용을 메일 메시지에 저장 (직렬화) 하는 파일 저장 명령과 동일 합니다. 이 구현은 사용자의 컴퓨터에서 메일 클라이언트에 대해를 호출 하 여 메일 주소를 지정 하 고 메일 메시지에 제목과 메시지 텍스트를 추가할 수 있는 기회를 사용자에 게 제공 합니다. 사용자에 게 친숙 한 메일 응용 프로그램의 사용자 인터페이스가 표시 됩니다. 이 기능은 및의 두 멤버 함수에서 제공 됩니다 `CDocument` . `OnFileSendMail` `OnUpdateFileSendMail`

MAPI는 첨부 파일을 보내기 위해 파일을 읽어야 합니다. 함수 호출 중에 응용 프로그램에서 데이터 파일을 열어 둔 경우 `OnFileSendMail` 여러 프로세스에서 파일에 액세스할 수 있도록 공유 모드를 사용 하 여 파일을 열어야 합니다.

> [!NOTE]
> For 클래스의 재정의 버전은 `OnFileSendMail` `COleDocument` 복합 문서를 올바르게 처리 합니다.

#### <a name="to-implement-a-send-mail-command-with-mfc"></a>MFC를 사용 하 여 메일 보내기 명령을 구현 하려면

1. Visual C++ 메뉴 편집기를 사용 하 여 명령 ID가 ID_FILE_SEND_MAIL 인 메뉴 항목을 추가 합니다.

   AFXRES.H의 프레임 워크에서이 명령 ID를 제공 합니다. 이 명령은 모든 메뉴에 추가할 수 있지만 일반적으로 **파일** 메뉴에 추가 됩니다.

1. 문서의 메시지 맵에 다음을 수동으로 추가 합니다.

   [!code-cpp[NVC_MFCDocView#9](codesnippet/cpp/mapi-support-in-mfc_1.cpp)]

    > [!NOTE]
    >  이 메시지 맵은 또는에서 파생 된 문서에 대해 작동 합니다 `CDocument` `COleDocument` . 메시지 맵이 파생 된 문서 클래스에 있는 경우에도 두 경우 모두 올바른 기본 클래스를 선택 합니다.

1. 응용 프로그램을 빌드합니다.

메일 지원을 사용할 수 있는 경우 MFC는를 사용 하 여 메뉴 항목을 사용 하도록 설정한 `OnUpdateFileSendMail` 다음를 사용 하 여 명령을 처리 `OnFileSendMail` 합니다. 메일 지원을 사용할 수 없는 경우에는 사용자가 메뉴 항목을 볼 수 없도록 MFC에서 자동으로 메뉴 항목을 제거 합니다.

> [!TIP]
> 앞에서 설명한 대로 메시지 맵 항목을 수동으로 추가 하는 대신 클래스 [클래스 마법사](reference/mfc-class-wizard.md) 를 사용 하 여 메시지를 함수에 매핑할 수 있습니다. 자세한 내용은 [함수에 메시지 매핑](reference/mapping-messages-to-functions.md)을 참조 하세요.

관련 정보는 [MAPI](mapi.md) 개요를 참조 하세요.

`CDocument`MAPI를 사용 하는 멤버 함수에 대 한 자세한 내용은 다음을 참조 하십시오.

- [CDocument:: OnFileSendMail](reference/cdocument-class.md#onfilesendmail)

- [CDocument:: OnUpdateFileSendMail](reference/cdocument-class.md#onupdatefilesendmail)

- [COleDocument:: OnFileSendMail](reference/coledocument-class.md#onfilesendmail)

## <a name="see-also"></a>참고 항목

[MAPI](mapi.md)
