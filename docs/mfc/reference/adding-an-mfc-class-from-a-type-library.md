---
description: '자세히 알아보기: 형식 라이브러리에서 MFC 클래스 추가'
title: 형식 라이브러리에서 MFC 클래스 추가
ms.date: 11/04/2016
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
ms.openlocfilehash: b5a9979e2581eb3a560736c57c4b1eac4a7e1e81
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248374"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>형식 라이브러리에서 MFC 클래스 추가

이 마법사를 사용 하 여 사용 가능한 형식 라이브러리의 인터페이스에서 MFC 클래스를 만들 수 있습니다. MFC 클래스를 [MFC 애플리케이션](../../mfc/reference/creating-an-mfc-application.md), [MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md) 또는 [MFC ActiveX 컨트롤](../../mfc/reference/creating-an-mfc-activex-control.md)에 추가할 수 있습니다.

> [!NOTE]
> 자동화를 사용 하 여 형식 라이브러리에서 클래스를 추가할 때 MFC 프로젝트를 만들 필요가 없습니다.

형식 라이브러리에는 구성 요소에서 노출 하는 인터페이스에 대 한 이진 설명이 포함 되어 있으며, 해당 매개 변수 및 반환 형식과 함께 메서드를 정의 합니다. Typelib의 클래스 추가 마법사에서 **사용 가능한 형식 라이브러리** 목록에 표시 하려면 해당 형식 라이브러리를 등록 해야 합니다.

### <a name="to-add-an-mfc-class-from-a-type-library"></a>형식 라이브러리에서 MFC 클래스를 추가 하려면

1. **솔루션 탐색기** 또는 [클래스 뷰](/visualstudio/ide/viewing-the-structure-of-code)에서 클래스를 추가 하려는 프로젝트의 이름을 마우스 오른쪽 단추로 클릭 합니다.

1. 바로 가기 메뉴에서 **추가** 를 클릭한 다음, **클래스 추가** 를 클릭합니다.

1. [클래스 추가](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) 대화 상자의 템플릿 창에서 **Typelib의 MFC 클래스** 를 클릭 한 다음 **열기** 를 클릭 하 여 [typelib에서 클래스 추가 마법사](../../mfc/reference/add-class-from-typelib-wizard.md)를 표시 합니다.

마법사에서 형식 라이브러리에 둘 이상의 클래스를 추가할 수 있습니다. 마찬가지로, 단일 마법사 세션에서 두 개 이상의 형식 라이브러리에 있는 클래스를 추가할 수 있습니다.

마법사는 선택한 형식 라이브러리에서 추가 하는 각 인터페이스에 대해 [Coledispatchdriver](../../mfc/reference/coledispatchdriver-class.md)에서 파생 된 MFC 클래스를 만듭니다. `COleDispatchDriver` OLE 자동화의 클라이언트 쪽을 구현 합니다.

## <a name="see-also"></a>참고 항목

[자동화 클라이언트](../../mfc/automation-clients.md)<br/>
[자동화 클라이언트: 형식 라이브러리 사용](../../mfc/automation-clients-using-type-libraries.md)
