---
description: '자세히 알아보기: 서버: 서버 구현'
title: '서버: 서버 구현'
ms.date: 11/04/2016
helpviewer_keywords:
- servers, implementing
- OLE server applications [MFC], implementing OLE servers
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
ms.openlocfilehash: 3ced10f88ce062ab571841610ba4b000571835b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217382"
---
# <a name="servers-implementing-a-server"></a>서버: 서버 구현

이 문서에서는 MFC 응용 프로그램 마법사가 비주얼 편집 서버 응용 프로그램을 위해 만드는 코드를 설명 합니다. 응용 프로그램 마법사를 사용 하지 않는 경우이 문서에서는 서버 응용 프로그램을 구현 하는 코드를 작성 해야 하는 영역을 나열 합니다.

응용 프로그램 마법사를 사용 하 여 새 서버 응용 프로그램을 만드는 경우 서버 관련 코드를 상당히 많이 제공 합니다. 기존 응용 프로그램에 시각적 편집 서버 기능을 추가 하는 경우 필요한 나머지 서버 코드를 추가 하기 전에 응용 프로그램 마법사에서 제공한 코드를 복제 해야 합니다.

응용 프로그램 마법사에서 제공 하는 서버 코드는 다음과 같은 여러 범주에 속합니다.

- 서버 리소스 정의:

  - 서버가 자체 창에서 포함 된 항목을 편집 하는 경우 사용 되는 메뉴 리소스입니다.

  - 서버를 현재 상태로 둘 때 사용 하는 메뉴 및 도구 모음 리소스입니다.

  이러한 리소스에 대 한 자세한 내용은 [메뉴 및 리소스: 서버 추가](../mfc/menus-and-resources-server-additions.md)를 참조 하세요.

- 에서 파생 된 항목 클래스를 정의 `COleServerItem` 합니다. 서버 항목에 대 한 자세한 내용은 서버 [: 서버 항목](../mfc/servers-server-items.md)을 참조 하세요.

- 문서 클래스의 기본 클래스를로 변경 `COleServerDoc` 합니다. 자세한 내용은 서버 [: 서버 문서 구현](../mfc/servers-implementing-server-documents.md)을 참조 하세요.

- 에서 파생 되는 프레임 창 클래스를 정의 `COleIPFrameWnd` 합니다. 자세한 내용은 [서버: In-Place 프레임 창 구현](../mfc/servers-implementing-in-place-frame-windows.md)을 참조 하세요.

- Windows 등록 데이터베이스에서 서버 응용 프로그램에 대 한 항목을 만들고 OLE 시스템에 서버의 새 인스턴스를 등록 합니다. 이 항목에 대 한 자세한 내용은 [등록](../mfc/registration.md)을 참조 하세요.

- 서버 응용 프로그램 초기화 및 시작 이 항목에 대 한 자세한 내용은 [등록](../mfc/registration.md)을 참조 하세요.

자세한 내용은 *클래스 라이브러리 참조* 에서 [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerDoc](../mfc/reference/coleserverdoc-class.md)및 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[서버](../mfc/servers.md)<br/>
[컨테이너](../mfc/containers.md)<br/>
[메뉴 및 리소스 (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[등록](../mfc/registration.md)
