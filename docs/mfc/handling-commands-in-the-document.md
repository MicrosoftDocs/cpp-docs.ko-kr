---
description: '자세한 정보: 문서에서 명령 처리'
title: 문서에서 명령 처리
ms.date: 11/04/2016
helpviewer_keywords:
- message maps [MFC], in document class
- command handling [MFC]
- documents [MFC], message maps
- message handling [MFC], WM_COMMAND messages
- command handling [MFC], commands in documents
- documents [MFC], handling messages in
ms.assetid: c7375584-27af-4275-b2fd-afea476785d0
ms.openlocfilehash: 4d8252cb16eee0e1c5c802e5839ec925a7879cc5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248894"
---
# <a name="handling-commands-in-the-document"></a>문서에서 명령 처리

문서 클래스는 메뉴 항목, 도구 모음 단추 또는 액셀러레이터 키로 생성 된 특정 명령을 처리할 수도 있습니다. 기본적으로는 `CDocument` serialization을 사용 하 여 파일 메뉴의 저장 및 다른 이름으로 저장 명령을 처리 합니다. 데이터에 영향을 주는 다른 명령은 문서의 멤버 함수에 의해 처리 될 수도 있습니다. 예를 들어, Scribble 프로그램에서 클래스는 `CScribDoc` 편집 모두 지우기 명령에 대 한 처리기를 제공 하 여 문서에 현재 저장 되어 있는 모든 데이터를 삭제 합니다. 문서는 메시지 맵을 포함할 수 있지만 뷰와 달리 문서는 표준 Windows 메시지를 처리할 수 없습니다. **WM_COMMAND** 메시지만 또는 "명령"입니다.

## <a name="see-also"></a>참고 항목

[문서 사용](using-documents.md)
