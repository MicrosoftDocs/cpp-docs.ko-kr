---
description: '자세히 알아보기: 여러 문서 형식, 뷰 및 프레임 창'
title: 여러 문서 형식, 뷰 및 프레임 창
ms.date: 11/19/2018
helpviewer_keywords:
- static splitter windows [MFC]
- multiple views [MFC]
- multiple document types [MFC]
- multiple views [MFC], frame windows
- document classes [MFC], multiple
- documents [MFC], multiple types of
- splitter windows [MFC], dynamic
- dynamic splitter windows [MFC]
- windows [MFC], dynamic splitter
- windows [MFC], static splitter
- multiple frame windows [MFC]
- splitter windows [MFC], static
ms.assetid: c6b9e4e0-7c9c-45f1-a804-aeac39c9a128
ms.openlocfilehash: 05af9f0a86210804f7f83d82d9c18ddb80e47a4e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275596"
---
# <a name="multiple-document-types-views-and-frame-windows"></a>여러 문서 형식, 뷰 및 프레임 창

문서, 뷰 및 프레임 창의 기본 관계는 [문서/뷰 만들기](document-view-creation.md)에서 설명합니다. 대부분의 애플리케이션은 단일한 뷰와 문서당 하나의 프레임 창만 사용하는 단일한 문서 형식(그러나 해당 형식의 문서는 여러 개 열 수 있음)을 지원합니다. 그러나 일부 애플리케이션에서는 이러한 기본 설정을 하나 이상 변경해야 할 수도 있습니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [Multiple document types](#_core_multiple_document_types)

- [여러 보기](#_core_multiple_views)

- [Multiple frame windows](#_core_multiple_frame_windows)

- [분할자 창](#_core_splitter_windows)

## <a name="multiple-document-types"></a><a name="_core_multiple_document_types"></a> 여러 문서 형식

MFC 애플리케이션 마법사는 기본적으로 하나의 문서 클래스를 만듭니다. 그러나 일부 경우 문서 형식을 하나 이상 지원해야 할 수도 있습니다. 예를 들어, 애플리케이션에 워크시트와 차트 문서가 모두 필요할 수 있습니다. 각 문서 형식은 고유한 문서 클래스로 나타내며 가능하면 뷰 클래스로도 나타냅니다. 사용자가 파일 메뉴에서 새로 만들기 명령을 선택하면 프레임워크에서 지원 문서 형식이 나열된 대화 상자를 표시합니다. 그런 다음 사용자가 선택한 형식의 문서를 만듭니다. 각 문서 형식은 고유한 문서 템플릿 개체에서 관리합니다.

문서 클래스를 더 만들려면 [클래스 추가](../ide/adding-a-class-visual-cpp.md)를 참조하세요. 파생시킬 클래스 형식으로 [CDocument](reference/cdocument-class.md) 를 선택하고 요청된 문서 정보를 제공합니다. 그런 다음 새 클래스의 데이터를 구현합니다.

프레임워크에 추가 문서 클래스에 대한 정보를 알리려면 애플리케이션 클래스의 [InitInstance](reference/cwinapp-class.md#adddoctemplate) 재정의에 [AddDocTemplate](reference/cwinapp-class.md#initinstance) 에 대한 두 번째 호출을 추가해야 합니다. 자세한 내용은 [문서 템플릿](document-templates-and-the-document-view-creation-process.md)을 참조하세요.

## <a name="multiple-views"></a><a name="_core_multiple_views"></a> 여러 뷰

대부분의 문서에는 하나의 뷰만 필요하지만 단일 문서의 뷰를 하나 이상 지원할 수도 있습니다. 다중 뷰를 구현하려면 문서 개체에 문서의 뷰 목록, 뷰를 추가 및 제거하는 멤버 함수, 문서의 데이터가 변경될 때 다중 뷰에 알리는 [UpdateAllViews](reference/cdocument-class.md#updateallviews) 멤버 함수가 있어야 합니다.

MFC는 같은 문서에 대한 다중 뷰가 필요한 세 가지 공용 사용자 인터페이스를 지원합니다. 이러한 모델은 다음과 같습니다.

- 각각 별도의 MDI 문서 프레임 창에 표시되는 같은 클래스의 뷰 개체

   문서에 대한 두 번째 프레임 창 만들기를 지원할 수도 있습니다. 사용자는 새 창 명령을 선택하여 같은 문서의 뷰가 표시된 두 번째 프레임을 연 다음 두 개의 프레임을 사용하여 문서의 다른 부분을 동시에 볼 수 있습니다. 프레임워크는 초기 프레임 창과 문서에 연결된 뷰를 복제하여 MDI 애플리케이션 창 메뉴의 새 창 명령을 지원합니다.

- 같은 문서 프레임 창에 있는 같은 클래스의 뷰 개체

   분할 창은 단일 문서 창의 뷰 공간을 여러 개의 분리된 문서 뷰로 분할합니다. 프레임워크는 같은 뷰 클래스로부터 여러 개의 뷰 개체를 만듭니다. 자세한 내용은 [분할 창](#_core_splitter_windows)을 참조하세요.

- 단일한 프레임 창에 있는 서로 다른 클래스의 뷰 개체

   이 모델에서 여러 개의 분할 창으로 구성된 다중 뷰는 단일한 프레임 창을 공유합니다. 여러 클래스에서 뷰를 만들고 각 뷰마다 같은 문서를 다르게 표시합니다. 예를 들어, 한 뷰에는 워드 프로세서 문서를 표준 모드로 표시하고 다른 뷰에는 같은 문서를 개요 모드로 표시할 수 있습니다. 분할자 컨트롤을 사용하면 사용자가 뷰의 상대 크기를 조정할 수 있습니다.

다음 그림은 a, b, 및 c로 나누어 세 개의 사용자 인터페이스 모델을 위에서 설명한 순서로 보여 줍니다.

![다중&#45;뷰 사용자 인터페이스](../mfc/media/vc37a71.gif "다중&#45;뷰 사용자 인터페이스") <br/>
여러 뷰 사용자 인터페이스

프레임워크에서는 새 창 명령을 구현하고 [분할 창](reference/csplitterwnd-class.md)에서 설명한 대로 [CSplitterWnd](#_core_splitter_windows)클래스를 제공하여 이 세 가지 모델을 제공합니다. 이 방법으로 시작하여 다른 모델을 구현할 수도 있습니다. 다른 구성의 뷰, 프레임 창 및 분할 창을 보여 주는 샘플 프로그램은 [MFC 샘플](../overview/visual-cpp-samples.md#mfc-samples)을 참조하세요.

`UpdateAllViews`에 대한 자세한 내용은 [MFC 참조](reference/cview-class.md) 의 *CView* 클래스 및 [SCRIBBLE 샘플](../overview/visual-cpp-samples.md)을 참조하세요.

## <a name="multiple-frame-windows"></a><a name="_core_multiple_frame_windows"></a> 다중 프레임 창

MDI 애플리케이션 창 메뉴의 새 창 명령을 사용하면 같은 문서에 두 번째 프레임 창을 만들 수 있습니다. 자세한 내용은 다중 뷰 사용자 인터페이스 그림의 첫 번째 모델을 참조하세요.

## <a name="splitter-windows"></a><a name="_core_splitter_windows"></a> 분할자 창

분할 창에서 창은 둘 이상의 스크롤 가능한 창으로 분할되어 있거나 분할할 수 있습니다. 스크롤 막대 옆에 있는 창 프레임의 분할자 컨트롤(또는 "나눔줄")을 사용하면 사용자가 창의 상대 크기를 조정할 수 있습니다. 각 창은 같은 문서에 대한 뷰입니다. "동적" 분할 창에서는 다중 뷰 사용자 인터페이스 그림의 b 부분에 표시된 것처럼 뷰의 클래스가 같습니다. "정적" 분할 창에서는 뷰의 클래스가 다를 수 있습니다. [CSplitterWnd](reference/csplitterwnd-class.md)클래스는 두 가지 종류의 분할 창을 모두 지원합니다.

같은 클래스의 뷰로 구성된 동적 분할 창을 사용하면 사용자가 임의로 창을 다중 창으로 분할한 다음 각 창을 스크롤하여 문서의 각 부분을 확인할 수 있습니다. 또한 사용자가 창의 분할을 해제하여 추가 뷰를 제거할 수도 있습니다. [SCRIBBLE 샘플](../overview/visual-cpp-samples.md) 에 추가된 분할 창은 이에 대한 예제입니다. 해당 항목은 동적 분할 창을 만드는 방법을 설명합니다. 동적 분할 창은 다중 뷰 사용자 인터페이스 그림의 b 부분에 표시되어 있습니다.

다른 클래스의 뷰로 구성된 정적 분할 창은 각각 용도가 다른 다중 창으로 분할된 창으로 시작합니다. 예를 들어, Visual C++ 비트맵 편집기의 이미지 창에는 두 개의 창이 나란히 표시됩니다. 왼쪽 창에는 비트맵이 실제 크기로 표시되고 오른쪽 창에는 같은 비트맵의 확대된 이미지가 표시됩니다. 창은 사용자가 끌어서 창의 상대 크기를 변경할 수 있는 "분할 막대"로 분리되어 있습니다. 정적 분할 창은 다중 뷰 사용자 인터페이스 그림의 c 부분에 표시되어 있습니다.

자세한 내용은 [MFC 참조](reference/csplitterwnd-class.md) 의 *CSplitterWnd* 클래스 및 [MFC 샘플](../overview/visual-cpp-samples.md#mfc-samples)을 참조하세요.

## <a name="see-also"></a>참고 항목

[문서/뷰 아키텍처](document-view-architecture.md)
