---
description: '자세히 알아보기: 문서 템플릿 및 문서/뷰 만들기 프로세스'
title: 문서 템플릿 및 Document-View 만들기 프로세스
ms.date: 11/19/2018
helpviewer_keywords:
- icons, for multiple document templates
- document templates [MFC], and views
- document/view architecture [MFC], creating document/view
- single document template
- MFC, document templates
- multiple document template
- CDocTemplate class [MFC]
- templates [MFC], document templates
ms.assetid: 311ce4cd-fbdf-4ea1-a51b-5bb043abbcee
ms.openlocfilehash: 324d46df1027c03e7f41564691742c5c065cf85c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330249"
---
# <a name="document-templates-and-the-documentview-creation-process"></a>문서 템플릿 및 문서/뷰 만들기 프로세스

관련 보기 및 프레임 창으로 문서를 만드는 복잡 한 프로세스를 관리 하기 위해 프레임 워크는 두 개의 문서 템플릿 클래스인 SDI 응용 프로그램용 [Csingledoctemplate](reference/csingledoctemplate-class.md) 및 MDI 응용 프로그램용 [csingledoctemplate](reference/cmultidoctemplate-class.md) 을 사용 합니다. 는 한 `CSingleDocTemplate` 번에 하나의 형식의 문서를 만들고 저장할 수 있습니다. 는 `CMultiDocTemplate` 한 형식의 여러 열린 문서 목록을 보관 합니다.

일부 응용 프로그램은 여러 문서 형식을 지원 합니다. 예를 들어 응용 프로그램은 텍스트 문서와 그래픽 문서를 지원할 수 있습니다. 이러한 응용 프로그램에서는 사용자가 파일 메뉴에서 새로 만들기 명령을 선택 하면 대화 상자에 새 문서 유형을 열 수 있는 목록이 표시 됩니다. 응용 프로그램은 지원 되는 각 문서 형식에 대해 고유한 문서 템플릿 개체를 사용 합니다. 다음 그림에서는 두 개의 문서 유형을 지 원하는 MDI 응용 프로그램의 구성을 보여 주고 여러 문서를 보여 줍니다.

![2가지 문서 형식이 포함된 MDI 응용 프로그램](../mfc/media/vc387h1.gif "2가지 문서 형식이 포함된 MDI 응용 프로그램") <br/>
두 문서 형식을 사용하는 MDI 애플리케이션

문서 템플릿은 응용 프로그램 개체에 의해 생성 되 고 유지 관리 됩니다. 응용 프로그램의 기능 중에 수행 되는 주요 작업 중 하나는 `InitInstance` 적절 한 종류의 문서 템플릿을 하나 이상 생성 하는 것입니다. 이 기능은 [문서 템플릿 만들기](document-template-creation.md)에 설명 되어 있습니다. 응용 프로그램 개체는 템플릿 목록의 각 문서 템플릿에 대 한 포인터를 저장 하 고 문서 템플릿을 추가 하기 위한 인터페이스를 제공 합니다.

두 개 이상의 문서 유형을 지원 해야 하는 경우 각 문서 유형별로 [Adddoctemplate](reference/cwinapp-class.md#adddoctemplate) 에 대 한 추가 호출을 추가 해야 합니다.

응용 프로그램의 문서 템플릿 목록에서 해당 위치를 기준으로 각 문서 템플릿에 대해 아이콘이 등록 됩니다. 문서 템플릿의 순서는를 호출 하 여 추가 되는 순서에 따라 결정 됩니다 `AddDocTemplate` . MFC는 응용 프로그램의 첫 번째 아이콘 리소스가 응용 프로그램 아이콘이 고 다음 아이콘 리소스가 첫 번째 문서 아이콘 일 것으로 가정 합니다.

예를 들어 문서 템플릿은 응용 프로그램에 대 한 세 번째의 세 번째입니다. 인덱스 3의 응용 프로그램에 아이콘 리소스가 있으면 해당 아이콘이 문서 템플릿에 사용 됩니다. 그렇지 않으면 인덱스 0의 아이콘이 기본값으로 사용 됩니다.

## <a name="see-also"></a>참고 항목

[일반 MFC 항목](general-mfc-topics.md)<br/>
[문서 템플릿 만들기](document-template-creation.md)<br/>
[문서/뷰 만들기](document-view-creation.md)<br/>
[MFC 개체 간 관계](relationships-among-mfc-objects.md)<br/>
[새 문서, 창 및 뷰 만들기](creating-new-documents-windows-and-views.md)
