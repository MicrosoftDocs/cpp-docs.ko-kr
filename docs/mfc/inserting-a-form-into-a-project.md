---
description: '자세히 알아보기: 프로젝트에 폼 삽입'
title: 프로젝트에 폼 삽입
ms.date: 11/04/2016
helpviewer_keywords:
- inserting forms [MFC]
- Insert New dialog box [MFC]
- forms, adding to projects
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
ms.openlocfilehash: d0c67532261e4c5a5740f4ff07543f141b34d7a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220489"
---
# <a name="inserting-a-form-into-a-project"></a>프로젝트에 폼 삽입

폼은 컨트롤에 대 한 편리한 컨테이너를 제공 합니다. 응용 프로그램이 MFC 라이브러리를 지 원하는 한 MFC 기반 폼을 응용 프로그램에 쉽게 삽입할 수 있습니다.

### <a name="to-insert-a-form-into-your-project"></a>프로젝트에 폼을 삽입 하려면

1. 클래스 뷰에서 양식을 추가 하려는 프로젝트를 선택 하 고 마우스 오른쪽 단추를 클릭 합니다.

1. 바로 가기 메뉴에서 **추가** 를 클릭 한 다음 **클래스 추가** 를 클릭 합니다.

   **새 양식** 명령을 사용할 수 없는 경우 프로젝트는 ATL (액티브 템플릿 라이브러리)을 기반으로 할 수 있습니다. ATL 프로젝트에 폼을 추가 하려면 프로젝트를 처음 만들 때 [특정 설정을 지정](../atl/reference/application-settings-atl-project-wizard.md) 해야 합니다.

1. **Mfc** 폴더에서 **mfc 클래스** 를 클릭 합니다.

1. MFC 클래스 마법사를 사용 하 여 새 클래스가 [CFormView](reference/cformview-class.md)에서 파생 되도록 합니다.

Visual C++ 폼을 응용 프로그램에 추가 하 여 대화 상자 편집기에서 열면 컨트롤을 추가 하 고 전체 디자인 작업을 시작할 수 있습니다.

다음과 같은 추가 단계를 수행 해야 할 수 있습니다 (대화 상자 기반 응용 프로그램에는 해당 되지 않음).

1. `OnUpdate`멤버 함수를 재정의 합니다.

1. 뷰에서 문서로 데이터를 이동 하는 멤버 함수를 구현 합니다.

1. `OnPrint`멤버 함수를 만듭니다.

## <a name="see-also"></a>참고 항목

[폼 뷰](form-views-mfc.md)
