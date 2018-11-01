---
title: 새 문서, 창 및 뷰 만들기
ms.date: 11/04/2016
helpviewer_keywords:
- MDI [MFC], creating windows
- window objects [MFC], creating
- objects [MFC], creating document objects
- MFC default objects
- frame windows [MFC], creating
- windows [MFC], MDI
- MFC, documents
- view objects [MFC], creating
- windows [MFC], creating
- overriding, default view behavior
- views [MFC], initializing
- customizing MFC default objects
- MFC, frame windows
- MFC, views
- MDI [MFC], frame windows
- child windows [MFC], creating MDI
- view objects [MFC]
- document objects [MFC], creating
- MFC default objects [MFC], customizing
- views [MFC], overriding default behavior
- initializing views [MFC]
ms.assetid: 88aa1f5f-2078-4603-b16b-a2b4c7b4a2a3
ms.openlocfilehash: 20bc94c7a688d3cf88fa89fff060ab155d327606
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643900"
---
# <a name="creating-new-documents-windows-and-views"></a>새 문서, 창 및 뷰 만들기

다음 그림에서는 문서, 뷰 및 프레임 창 만들기 프로세스의 개요를 제공합니다. 참여 하는 개체에 중점을 둔 다른 문서는 추가 세부 정보를 제공 합니다.

이 프로세스를 완료 하면 협동 개체가 존재 하 고 서로에 대 한 포인터를 저장 합니다. 다음 그림에서는 개체 생성 하는 시퀀스를 보여 줍니다. 그림에는 순서를 따를 수 있습니다.

![문서 만들기 시퀀스](../mfc/media/vc387l1.gif "vc387l1") 문서 만들기 시퀀스

![프레임 창 만들기 시퀀스](../mfc/media/vc387l2.png "vc387l2") 프레임 창 만들기 시퀀스

![뷰를 만드는 순서](../mfc/media/vc387l3.gif "vc387l3") 뷰 만들기 시퀀스

프레임 워크를 새 문서, 뷰 및 프레임 창 개체를 초기화 하는 방법에 대 한 내용은 클래스를 참조 하십시오 [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md)를 [CFrameWnd](../mfc/reference/cframewnd-class.md)합니다 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), 및 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) MFC 라이브러리 참조에서 합니다. 도 참조 하세요 [Technical Note 22](../mfc/tn022-standard-commands-implementation.md), 해당 프레임 워크의 표준 명령에 대 한 설명은 아래 추가로 생성 및 초기화 프로세스를 설명 하는 합니다 **새로 만들기** 및 **엽니다** 항목에 **파일** 메뉴.

##  <a name="_core_initializing_your_own_additions_to_these_classes"></a> 이러한 클래스에 대 한 고유한 추가 초기화

앞의 그림에 제안할 요소는 응용 프로그램의 개체를 초기화 하는 멤버 함수를 재정의할 수 있습니다. 재정의 `OnInitialUpdate` 뷰 클래스의 뷰를 초기화 하는 것이 좋습니다. `OnInitialUpdate` 호출 프레임 창을 만들고 보기 프레임 창 내에서 해당 문서에 첨부 된 직후에 발생 합니다. 예를 들어 보기는 스크롤 보기 (에서 파생 된 `CScrollView` 대신 `CView`), 문서 크기에 따라 뷰 크기를 설정 해야 사용자 `OnInitialUpdate` 재정의 합니다. (이 프로세스는 클래스의 설명에 설명 되어 [CScrollView](../mfc/reference/cscrollview-class.md).) 재정의할 수 있습니다 합니다 `CDocument` 멤버 함수 `OnNewDocument` 및 `OnOpenDocument` 문서의 응용 프로그램 관련 초기화를 제공 합니다. 일반적으로 모두 재정의 해야 하므로 두 가지 방법으로 문서를 만들 수 있습니다.

대부분의 경우에서 재정의 기본 클래스 버전을 호출 해야 합니다. 자세한 내용은 클래스의 명명 된 멤버 함수를 참조 하세요 [CDocument](../mfc/reference/cdocument-class.md)를 [CView](../mfc/reference/cview-class.md)를 [CFrameWnd](../mfc/reference/cframewnd-class.md), 및 [CWinApp](../mfc/reference/cwinapp-class.md) MFC에서 라이브러리 참조입니다.

## <a name="see-also"></a>참고 항목

[문서 템플릿 및 문서/뷰 만들기 프로세스](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[문서 템플릿 만들기](../mfc/document-template-creation.md)<br/>
[문서/뷰 만들기](../mfc/document-view-creation.md)<br/>
[MFC 개체 간 관계](../mfc/relationships-among-mfc-objects.md)

