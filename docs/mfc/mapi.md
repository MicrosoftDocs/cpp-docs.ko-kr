---
title: MAPI
ms.date: 11/04/2016
helpviewer_keywords:
- messaging [MFC], client applications
- enabling applications for MAPI [MFC]
- MAPI support in MFC
- e-mail [MFC], enabling
- mail [MFC], enabling your application
- MAPI, MFC
- enabling applications for mail [MFC]
ms.assetid: 193449f7-b131-4ab0-9301-8d4f6cd1e7c4
ms.openlocfilehash: a5f60e1ba8c2b68ddca312859694f532e38da965
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365164"
---
# <a name="mapi"></a>MAPI

이 문서에서는 클라이언트 메시지 응용 프로그램 개발자를 위한 Microsoft MAPI(메시징 응용 프로그래밍 인터페이스)에 대해 설명합니다. MFC 클래스에서 MAPI 하위 집합에 대 한 지원을 제공 `CDocument` 하지만 전체 API를 캡슐화 하지 않습니다. 자세한 내용은 [MFC의 MAPI 지원](../mfc/mapi-support-in-mfc.md)합니다.

MAPI는 메일 지원 및 메일 인식 응용 프로그램이 메일 메시지를 생성, 조작, 전송 및 저장할 수 있게 해주는 일련의 함수입니다. MAPI는 응용 프로그램 개발자가 메일 메시지의 목적 및 내용을 정의하고 저장된 메일 메시지를 유연한 방식으로 관리할 수 있게 해주는 도구를 제공합니다. MAPI는 또한 응용 프로그램 개발자가 기본 메시징 시스템과 독립적으로 메일 지원 및 메일 인식 응용 프로그램을 만드는 데 사용할 수 있는 공통 인터페이스를 제공합니다.

메시징 클라이언트는 Microsoft WMS(Windows Messaging System)와 상호 작용할 수 있는 휴먼 인터페이스를 제공합니다. 이러한 상호 작용에는 일반적으로 메시지 저장소 및 주소록과 같이 MAPI 호환 공급자의 서비스 요청이 포함됩니다.

MAPI에 대 한 자세한 내용은 Windows sdk 설명서의 Win32 메시징 (MAPI) 문서를 참조 하세요.

## <a name="in-this-section"></a>섹션 내용

[MFC의 MAPI 지원](../mfc/mapi-support-in-mfc.md)

## <a name="see-also"></a>참고자료

[CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)<br/>
[CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)<br/>
[COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)
