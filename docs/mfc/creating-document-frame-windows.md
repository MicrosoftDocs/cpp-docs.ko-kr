---
description: '자세히 알아보기: 문서 프레임 창 만들기'
title: 문서 프레임 창 만들기
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], creating
- document templates [MFC], and document frame windows
- windows [MFC], creating
- runtime, class information
- run-time class [MFC], and document frame window creation
- document frame windows [MFC], creating
- MFC, frame windows
ms.assetid: 8671e239-b76f-4dea-afa8-7024e6e58ff5
ms.openlocfilehash: e2c4f72ab56045df7bb121be3bb557314780fedb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309812"
---
# <a name="creating-document-frame-windows"></a>문서 프레임 창 만들기

[문서/뷰 만들기](document-view-creation.md) 는 [cdoctemplate](reference/cdoctemplate-class.md) 개체가 프레임 창, 문서 및 보기를 만들고 모두 함께 연결 하는 방법을 보여 오케스트레이션. 생성자에 대 한 세 개의 [CRuntimeClass](reference/cruntimeclass-structure.md) 인수는 `CDocTemplate` 파일 메뉴의 새 명령 또는 MDI 창 메뉴의 새 창 명령과 같은 사용자 명령에 따라 문서 템플릿이 동적으로 만드는 프레임 창, 문서 및 뷰 클래스를 지정 합니다. 문서 템플릿은 나중에 보기 및 문서에 대 한 프레임 창을 만들 때 사용할 수 있도록이 정보를 저장 합니다.

[RUNTIME_CLASS](reference/run-time-object-model-services.md#runtime_class) 메커니즘이 제대로 작동 하려면 [DECLARE_DYNCREATE](reference/run-time-object-model-services.md#declare_dyncreate) 매크로를 사용 하 여 파생 된 프레임 창 클래스를 선언 해야 합니다. 이는 프레임 워크가 클래스의 동적 생성 메커니즘을 사용 하 여 문서 프레임 창을 만들어야 하기 때문입니다 `CObject` .

사용자가 문서를 만드는 명령을 선택 하면 프레임 워크는 문서 템플릿을 호출 하 여 문서 개체, 뷰 및 뷰를 표시 하는 프레임 창을 만듭니다. 문서 프레임 창을 만들 때 문서 템플릿은 적절 한 클래스의 개체 (SDI 응용 프로그램의 경우 [CFrameWnd](reference/cframewnd-class.md) 에서 파생 된 클래스 또는 MDI 응용 프로그램의 경우 [CMDIChildWnd](reference/cmdichildwnd-class.md) )를 만듭니다. 그런 다음 프레임 워크는 프레임 창 개체의 [loadframe](reference/cframewnd-class.md#loadframe) 멤버 함수를 호출 하 여 리소스에서 생성 정보를 가져오고 Windows 창을 만듭니다. 프레임 워크는 창 핸들을 프레임 창 개체에 연결 합니다. 그런 다음 뷰를 문서 프레임 창의 자식 창으로 만듭니다.

파생 개체를 [초기화할 시기를 결정 하](when-to-initialize-cwnd-objects.md) 는 데 주의를 기울여야 `CWnd` 합니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [CObject에서 클래스 파생 (동적 생성 메커니즘)](deriving-a-class-from-cobject.md)

- [문서/뷰 만들기 (템플릿 및 프레임 창 생성)](document-view-creation.md)

- [프레임 창 제거](destroying-frame-windows.md)

## <a name="see-also"></a>참고 항목

[프레임 창 사용](using-frame-windows.md)
