---
description: '자세히 알아보기: 문서/뷰 만들기'
title: Document-View 만들기
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], creating
- views [MFC], and frame windows
- views [MFC], creating
- tables [MFC]
- MFC, views
- document/view architecture [MFC], creating document/view
- object creators
- MFC, documents
- tables [MFC], objects each MFC object creates
ms.assetid: bda14f41-ed50-439d-af9e-591174e7dd64
ms.openlocfilehash: 128b68eb53bd596ba2e4b4df4f2c5e865452fe2a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326437"
---
# <a name="documentview-creation"></a>문서/뷰 만들기

프레임 워크는 **파일** 메뉴에 있는 **새** 명령 및 **열기** 명령의 구현을 제공 합니다. 새 문서와 관련 보기 및 프레임 창을 만들면 응용 프로그램 개체, 문서 템플릿, 새로 만든 문서 및 새로 만든 프레임 창 간에 협조적으로 작업 하 게 됩니다. 다음 표에서는 개체를 만드는 개체를 요약 합니다.

### <a name="object-creators"></a>개체 작성자

|만든 이|만듭니다|
|-------------|-------------|
|애플리케이션 개체|문서 템플릿|
|문서 템플릿|문서|
|문서 템플릿|프레임 창|
|프레임 창|보기|

## <a name="see-also"></a>참고 항목

[문서 템플릿 및 문서/뷰 만들기 프로세스](document-templates-and-the-document-view-creation-process.md)<br/>
[문서 템플릿 만들기](document-template-creation.md)<br/>
[MFC 개체 간 관계](relationships-among-mfc-objects.md)<br/>
[새 문서, 창 및 뷰 만들기](creating-new-documents-windows-and-views.md)
