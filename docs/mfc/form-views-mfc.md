---
description: '자세히 알아보기: 폼 뷰 (MFC)'
title: 폼 뷰(MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- user interfaces [MFC], forms
- forms [MFC]
- applications [MFC], forms-based
- forms-based applications [MFC]
- forms [MFC], adding to applications
ms.assetid: efbe73c1-4ca4-4613-aac2-30d916e92c0e
ms.openlocfilehash: be0853c46509e92d758b38e6a3b7fbd993e9b700
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180366"
---
# <a name="form-views-mfc"></a>폼 뷰(MFC)

[폼 기반 응용 프로그램](reference/creating-a-forms-based-mfc-application.md) 을 포함 하 여 MFC 라이브러리를 지 원하는 모든 Visual C++ 응용 프로그램에 폼을 추가할 수 있습니다. 폼 기반 응용 프로그램은 해당 뷰 클래스가에서 파생 됩니다 `CFormView` . 양식을 지원 하기 위해 처음에 응용 프로그램을 만들지 않은 경우 새 양식을 삽입 하면 Visual C++이 지원을 추가 합니다. 기본 [문서/뷰 아키텍처](document-view-architecture.md)를 구현 하는 SDI 또는 MDI 응용 프로그램에서 사용자가 **새** 명령 (기본적으로 **파일** 메뉴에서)을 선택 하면 사용자에 게 사용 가능한 양식을 선택 하 라는 메시지가 표시 Visual C++.

SDI 응용 프로그램을 사용 하는 경우 사용자가 **새** 명령을 선택 하면 양식의 현재 인스턴스가 계속 실행 되지만 선택한 양식이 있는 응용 프로그램의 새 인스턴스 (있는 경우)가 생성 됩니다. MDI 응용 프로그램에서는 사용자가 **새** 명령을 선택할 때 폼의 현재 인스턴스가 계속 실행 됩니다.

> [!NOTE]
> 대화 상자 기반 응용 프로그램에 폼을 삽입할 수 있습니다. 여기에는 대화 상자 클래스가를 기반으로 `CDialog` 하 고 다른 하나는 뷰 클래스가 구현 되지 않습니다. 그러나 문서/뷰 아키텍처가 없으면 Visual C++에서 **파일**&#124;**새** 기능을 자동으로 구현 하지 않습니다. 사용자가 다양 한 속성 페이지를 사용 하 여 탭 대화 상자를 구현 하는 등의 추가 양식을 볼 수 있는 방법을 만들어야 합니다.

응용 프로그램에 새 양식을 삽입 하면 Visual C++ 다음을 수행 합니다.

- 사용자가 선택 하는 폼 스타일 클래스 ( `CFormView` ,, `CRecordView` `CDaoRecordView` 또는) 중 하나를 기반으로 하는 클래스를 만듭니다 `CDialog` .

- 적절 한 스타일을 사용 하 여 대화 상자 리소스를 만들거나, 클래스와 아직 연결 되지 않은 기존 대화 상자 리소스를 사용할 수 있습니다.

   기존 대화 상자 리소스를 선택 하는 경우 대화 상자의 속성 페이지를 사용 하 여 이러한 스타일을 설정 해야 할 수 있습니다. 대화 상자의 스타일에는 다음이 포함 되어야 합니다.

     **WS_CHILD**= On

     **WS_BORDER**= Off

     **WS_VISIBLE**= Off

     **WS_CAPTION**= Off

문서/뷰 아키텍처를 기반으로 하는 응용 프로그램의 경우 **새 양식** 명령 (클래스 뷰을 마우스 오른쪽 단추로 클릭)도 다음과 같이 수행 됩니다.

- 기반 클래스를 만듭니다. `CDocument`

   새 클래스를 만드는 대신 프로젝트에서 기존 기반 클래스를 사용할 수 있습니다 `CDocument` .

- `CDocument`문자열, 메뉴 및 아이콘 리소스를 사용 하 여에서 파생 된 문서 템플릿을 생성 합니다.

   템플릿의 기반으로 사용할 새 클래스를 만들 수도 있습니다.

- 응용 프로그램의 코드에에 대 한 호출을 추가 `AddDocumentTemplate` `InitInstance` 합니다.

   Visual C++는 새로 만드는 각 폼에 대해이 코드를 추가 하 여 사용자가 **새** 명령을 선택할 때 사용 가능한 폼 목록에 폼을 추가 합니다. 이 코드에는 새 폼 개체를 구성 하는 연결 된 문서, 뷰 및 프레임 클래스의 이름과 연결 된 리소스 ID가 포함 됩니다.

   문서 템플릿은 문서, 프레임 창 및 뷰 사이의 연결 역할을 합니다. 단일 문서에 대해 많은 템플릿을 만들 수 있습니다.

자세한 내용은 다음을 참조하세요.

- [Forms-Based 응용 프로그램 만들기](reference/creating-a-forms-based-mfc-application.md)

- [프로젝트에 폼 삽입](inserting-a-form-into-a-project.md)

## <a name="see-also"></a>참고 항목

[사용자 인터페이스 요소](user-interface-elements-mfc.md)
