---
description: '자세한 정보: Forms-Based MFC 응용 프로그램 만들기'
title: 폼 기반 MFC 애플리케이션 만들기
ms.date: 09/09/2019
f1_keywords:
- vc.appwiz.mfcforms.project
helpviewer_keywords:
- applications [MFC], forms-based
- forms-based applications [MFC]
ms.assetid: 048d2f7d-b60d-4386-ad8e-71d49af9c05e
ms.openlocfilehash: 2023f4f2c074ef1d0e3adf936cd4c31bd334b795
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343240"
---
# <a name="creating-a-forms-based-mfc-application"></a>폼 기반 MFC 애플리케이션 만들기

양식은 사용자가 데이터에 액세스 하 고 변경할 수 있는 컨트롤을 포함 하는 대화 상자입니다. 사용자가 선택한 폼에서 선택 하는 응용 프로그램을 개발할 수 있습니다. 일반적으로 폼 기반 응용 프로그램에서는 사용자가 **파일** 메뉴에서 **새로 만들기** 를 클릭 하 여 폼에 액세스할 수 있습니다. 사용자에 게 **파일** 메뉴의 **새** 옵션에 대 한 액세스 권한을 부여 하지 않는 대화 상자 기반 응용 프로그램도 폼 기반 응용 프로그램으로 간주 됩니다.

SDI (단일 문서 인터페이스), 폼 기반 응용 프로그램에서는 특정 폼의 인스턴스를 한 번에 하나만 실행할 수 있습니다. **파일** 메뉴의 **새로 만들기** 옵션에서 새 폼을 선택 하 여 SDI 폼 기반 응용 프로그램에서 동시에 여러 폼을 실행할 수 있습니다.

MDI (다중 문서 인터페이스), 폼 기반 응용 프로그램을 만드는 경우 응용 프로그램은 동일한 형식의 여러 인스턴스를 지원할 수 있습니다.

여러 최상위 문서를 지 원하는 응용 프로그램을 만드는 경우 데스크톱은 문서에 대 한 암시적 부모 이며 문서의 프레임은 응용 프로그램의 클라이언트 영역으로 제한 되지 않습니다. 각각 고유한 프레임, 메뉴 및 작업 표시줄 아이콘을 사용 하 여 문서의 여러 인스턴스를 열 수 있습니다. 문서의 후속 인스턴스를 개별적으로 닫을 수 있지만 초기 인스턴스의 **파일** 메뉴에서 **끝내기** 옵션을 선택 하면 응용 프로그램에서 모든 인스턴스를 닫습니다.

SDI, MDI 및 다중 최상위 문서 응용 프로그램은 모두 폼 기반 이며 문서/뷰 아키텍처를 사용 합니다.

모든 대화 상자 기반 응용 프로그램은 정의에 따라 폼을 기반으로 합니다. 대화 상자 기반 응용 프로그램은 문서/뷰 아키텍처를 사용 하지 않으므로 고유한 추가 폼에 대 한 만들기 및 액세스 방법을 관리 해야 합니다.

폼 기반 응용 프로그램의 기본 클래스는 [CFormView](cformview-class.md)입니다. 응용 프로그램에 데이터베이스 지원이 있는 경우에서 파생 되는 클래스를 선택할 수도 있습니다 `CFormView` . 폼은에서 상속 되는 모든 클래스에서 파생 되는 창입니다 `CFormView` `CFormView` .

[CView](cview-class.md)와 같은 기본 클래스를 사용 하는 경우에도 나중에에서 파생 된 [MFC 클래스를 추가](adding-an-mfc-class.md) 하 여 응용 프로그램을 폼 기반으로 만들 수 있습니다 `CFormView` .

마법사를 완료 한 후 프로젝트가 열리고 `CFormView` 또는에서 상속 되는 클래스를 `CFormView` 기본 클래스로 선택 하거나 대화 상자 기반 응용 프로그램을 만든 경우에는 Visual C++ 대화 상자 편집기를 엽니다. 이때 첫 번째 폼을 디자인할 준비가 되었습니다.

### <a name="to-begin-creating-a-forms-based-mfc-executable"></a>폼 기반 MFC 실행 파일 만들기를 시작 하려면

1. 폼 기반 MFC 응용 프로그램용 [Mfc 응용 프로그램 만들기](creating-an-mfc-application.md) 의 지침을 따릅니다.

1. MFC 응용 프로그램 마법사 [응용 프로그램 유형](application-type-mfc-application-wizard.md) 페이지에서 **문서/뷰 아키텍처 지원** 확인란을 선택 합니다.

1. **단일 문서**, **여러 문서** 또는 **여러 최상위 문서** 를 선택 합니다.

    > [!NOTE]
    >  SDI, MDI 또는 다중 최상위 문서 인터페이스 응용 프로그램을 선택한 경우 `CView` 마법사의 [생성 된 클래스](generated-classes-mfc-application-wizard.md) 페이지에서 응용 프로그램 뷰에 대 한 기본 클래스로가 기본적으로 설정 됩니다. 폼 기반 응용 프로그램을 만들려면를 `CFormView` 응용 프로그램 보기의 기본 클래스로 선택 해야 합니다. 마법사는 폼 기반 응용 프로그램에 대 한 인쇄 지원을 제공 하지 않습니다.

1. 마법사의 다른 페이지에서 원하는 다른 프로젝트 옵션을 설정 합니다.

1. **마침** 을 클릭 하 여 기본 응용 프로그램을 생성 합니다.

자세한 내용은 다음을 참조하세요.

- [파생 뷰 클래스](../derived-view-classes-available-in-mfc.md)

- [문서/뷰 아키텍처에 대 한 대안](../alternatives-to-the-document-view-architecture.md)

- [응용 프로그램 디자인 선택](../application-design-choices.md)

## <a name="see-also"></a>참고 항목

[MFC 응용 프로그램 마법사](mfc-application-wizard.md)<br/>
[폼 뷰](../form-views-mfc.md)<br/>
[MFC 응용 프로그램 Explorer-Style 파일 만들기](creating-a-file-explorer-style-mfc-application.md)<br/>
[웹 Browser-Style MFC 응용 프로그램 만들기](creating-a-web-browser-style-mfc-application.md)
