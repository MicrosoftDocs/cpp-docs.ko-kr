---
description: '자세한 정보: 새 문서, 창 및 뷰 만들기'
title: 새 문서, 창 및 뷰 만들기
ms.date: 11/19/2018
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
ms.openlocfilehash: 718d24d63811d4e3b5cc847b5d0ef69361c6fdf3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309877"
---
# <a name="creating-new-documents-windows-and-views"></a>새 문서, 창 및 뷰 만들기

다음 그림은 문서, 뷰 및 프레임 창의 생성 프로세스에 대 한 개요를 제공 합니다. 참여 하는 개체에 초점을 맞춘 다른 문서는 추가 정보를 제공 합니다.

이 프로세스가 완료 되 면 협동 개체가 존재 하 고 서로에 대 한 포인터를 저장 합니다. 다음 그림은 개체가 생성 되는 순서를 보여 줍니다. 그림에서 그림 까지의 시퀀스를 따를 수 있습니다.

![문서 만들기 시퀀스](../mfc/media/vc387l1.gif "문서 만들기 시퀀스") <br/>
문서를 만드는 순서

![프레임 창 만들기 시퀀스](../mfc/media/vc387l2.png "프레임 창 만들기 시퀀스") <br/>
프레임 창을 만드는 순서

![뷰 만들기 시퀀스](../mfc/media/vc387l3.gif "뷰 만들기 시퀀스") <br/>
뷰를 만드는 순서

프레임 워크가 새 문서, 뷰 및 프레임 창 개체를 초기화 하는 방법에 대 한 자세한 내용은 MFC 라이브러리 참조에서 [CDocument](reference/cdocument-class.md), [CView](reference/cview-class.md), [CFrameWnd](reference/cframewnd-class.md), [CMDIFrameWnd](reference/cmdiframewnd-class.md)및 [CMDIChildWnd](reference/cmdichildwnd-class.md) 클래스를 참조 하세요. 또한 **파일** 메뉴의 **새로** 만들기 및 **열기** 항목에 대 한 프레임 워크의 표준 명령에 대 한 설명에서 만들기 및 초기화 프로세스를 자세히 설명 하는 [Technical Note 22](tn022-standard-commands-implementation.md)를 참조 하세요.

## <a name="initializing-your-own-additions-to-these-classes"></a><a name="_core_initializing_your_own_additions_to_these_classes"></a> 이러한 클래스에 대 한 사용자 고유의 추가 초기화

또한 위의 그림은 멤버 함수를 재정의 하 여 응용 프로그램의 개체를 초기화할 수 있는 요소를 제안 합니다. 뷰 `OnInitialUpdate` 클래스에서를 재정의 하 여 뷰를 초기화 하는 것이 가장 좋습니다. `OnInitialUpdate`호출은 프레임 창이 생성 된 직후 발생 하며 프레임 창 내의 뷰가 해당 문서에 연결 됩니다. 예를 들어 뷰가 스크롤 보기 (대신에서 파생 됨) 인 경우 `CScrollView` `CView` 재정의의 문서 크기에 따라 보기 크기를 설정 해야 합니다 `OnInitialUpdate` . 이 프로세스는 [CScrollView](reference/cscrollview-class.md)클래스의 설명에 설명 되어 있습니다. 멤버 함수를 재정의 `CDocument` `OnNewDocument` `OnOpenDocument` 하 고 문서의 응용 프로그램별 초기화를 제공할 수 있습니다. 일반적으로 두 가지 방법으로 문서를 만들 수 있으므로 두 가지 모두를 재정의 해야 합니다.

대부분의 경우 재정의는 기본 클래스 버전을 호출 해야 합니다. 자세한 내용은 MFC 라이브러리 참조에서 [CDocument](reference/cdocument-class.md), [CView](reference/cview-class.md), [CFrameWnd](reference/cframewnd-class.md)및 [CWinApp](reference/cwinapp-class.md) 클래스의 명명 된 멤버 함수를 참조 하세요.

## <a name="see-also"></a>참고 항목

[문서 템플릿 및 문서/뷰 만들기 프로세스](document-templates-and-the-document-view-creation-process.md)<br/>
[문서 템플릿 만들기](document-template-creation.md)<br/>
[문서/뷰 만들기](document-view-creation.md)<br/>
[MFC 개체 간 관계](relationships-among-mfc-objects.md)
