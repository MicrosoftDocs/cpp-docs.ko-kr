---
description: '자세한 정보: 단일 문서에 여러 뷰 추가'
title: 단일 문서에 뷰 여러 개 추가
ms.date: 11/04/2016
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
ms.openlocfilehash: 84f50ad96e4c5939c7ee2e97f8babfaa5221b6f5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343733"
---
# <a name="adding-multiple-views-to-a-single-document"></a>단일 문서에 뷰 여러 개 추가

MFC (Microsoft Foundation Class) 라이브러리를 사용 하 여 만든 SDI (단일 문서 인터페이스) 응용 프로그램에서 각 문서 형식은 단일 뷰 형식과 연결 됩니다. 경우에 따라 문서의 현재 뷰를 새 뷰로 전환 하는 기능을 사용 하는 것이 좋습니다.

> [!TIP]
> 단일 문서에 대 한 여러 뷰를 구현 하는 방법에 대 한 추가 절차는 [CDocument:: AddView](reference/cdocument-class.md#addview) 및 [COLLECT](../overview/visual-cpp-samples.md) MFC 샘플을 참조 하세요.

새 `CView` 파생 클래스와 뷰를 동적으로 기존 MFC 응용 프로그램으로 전환 하기 위한 추가 코드를 추가 하 여이 기능을 구현할 수 있습니다.

단계는 다음과 같습니다.

- [기존 응용 프로그램 클래스 수정](#vcconmodifyexistingapplicationa1)

- [새 뷰 클래스 만들기 및 수정](#vcconnewviewclassa2)

- [새 보기 만들기 및 연결](#vcconattachnewviewa3)

- [전환 함수 구현](#vcconswitchingfunctiona4)

- [보기 전환에 대 한 지원 추가](#vcconswitchingtheviewa5)

이 항목의 나머지 부분에서는 다음을 가정 합니다.

- 파생 개체의 이름은 `CWinApp` 이 `CMyWinApp` 고, `CMyWinApp` mywinapp에 선언 되 고 정의 됩니다 *. H* 및 *Mywinapp. CPP*.

- `CNewView` 새 파생 개체의 이름이 며 `CView` , `CNewView` newview에서 선언 되 고 정의 됩니다 *. H* 및 *newview. CPP*.

## <a name="modify-the-existing-application-class"></a><a name="vcconmodifyexistingapplicationa1"></a> 기존 응용 프로그램 클래스 수정

응용 프로그램이 보기 간에 전환 하려면 뷰를 저장 하는 멤버 변수와 뷰를 전환 하는 메서드를 추가 하 여 응용 프로그램 클래스를 수정 해야 합니다.

Mywinapp의 선언에 다음 코드를 추가 `CMyWinApp` *합니다. H*:

[!code-cpp[NVC_MFCDocViewSDI#1](codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]

새 멤버 변수 및는 `m_pOldView` `m_pNewView` 현재 뷰와 새로 만든 멤버를 가리킵니다. 새 메서드 ( `SwitchView` )는 사용자가 요청 하는 경우 뷰를 전환 합니다. 메서드 본문은이 항목의 뒷부분에 나오는 [전환 함수 구현](#vcconswitchingfunctiona4)에 설명 되어 있습니다.

응용 프로그램 클래스를 마지막으로 수정 하려면 전환 함수에 사용 되는 Windows 메시지 (**WM_INITIALUPDATE**)를 정의 하는 새 헤더 파일을 포함 해야 합니다.

Mywinapp의 include 섹션에 다음 줄을 삽입 *합니다. CPP*:

[!code-cpp[NVC_MFCDocViewSDI#2](codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]

변경 내용을 저장 하 고 다음 단계를 계속 합니다.

## <a name="create-and-modify-the-new-view-class"></a><a name="vcconnewviewclassa2"></a> 새 뷰 클래스 만들기 및 수정

새 뷰 클래스 만들기는 클래스 뷰에서 사용할 수 있는 **새 클래스** 명령을 사용 하 여 쉽게 만들 수 있습니다. 이 클래스의 유일한 요구 사항은에서 파생 되는 것입니다 `CView` . 응용 프로그램에이 새 클래스를 추가 합니다. 프로젝트에 새 클래스를 추가 하는 방법에 대 한 자세한 내용은 [클래스 추가](../ide/adding-a-class-visual-cpp.md)를 참조 하세요.

프로젝트에 클래스를 추가한 후에는 일부 뷰 클래스 멤버의 액세스 가능성을 변경 해야 합니다.

*Newview를 수정 합니다. H* , **`protected`** **`public`** 생성자 및 소멸자에 대해 액세스 지정자를에서로 변경 합니다. 이렇게 하면 클래스를 동적으로 만들고 소멸 하 고 표시 되기 전에 뷰 모양을 수정할 수 있습니다.

변경 내용을 저장 하 고 다음 단계를 계속 합니다.

## <a name="create-and-attach-the-new-view"></a><a name="vcconattachnewviewa3"></a> 새 보기 만들기 및 연결

새 보기를 만들고 연결 하려면 `InitInstance` 응용 프로그램 클래스의 기능을 수정 해야 합니다. 새 뷰 개체를 만든 다음 `m_pOldView` `m_pNewView` 두 개의 기존 뷰 개체를 사용 하 여 및를 모두 초기화 하는 새 코드가 추가 됩니다.

새 뷰는 함수 내에서 만들어지므로 `InitInstance` 새 뷰와 기존 뷰는 모두 응용 프로그램의 수명 동안 지속 됩니다. 그러나 응용 프로그램은 새 보기를 동적으로 손쉽게 만들 수 있습니다.

호출 후 다음 코드를 삽입 합니다 `ProcessShellCommand` .

[!code-cpp[NVC_MFCDocViewSDI#3](codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]

변경 내용을 저장 하 고 다음 단계를 계속 합니다.

## <a name="implement-the-switching-function"></a><a name="vcconswitchingfunctiona4"></a> 전환 함수 구현

이전 단계에서는 새 뷰 개체를 만들고 초기화 하는 코드를 추가 했습니다. 마지막 주요 부분은 전환 메서드인를 구현 하는 것입니다 `SwitchView` .

응용 프로그램 클래스에 대 한 구현 파일 (Mywinapp)의 끝에 *있습니다. CPP*)에서 다음 메서드 정의를 추가 합니다.

[!code-cpp[NVC_MFCDocViewSDI#4](codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]

변경 내용을 저장 하 고 다음 단계를 계속 합니다.

## <a name="add-support-for-switching-the-view"></a><a name="vcconswitchingtheviewa5"></a> 보기 전환에 대 한 지원 추가

최종 단계에는 `SwitchView` 응용 프로그램에서 뷰 간을 전환 해야 할 때 메서드를 호출 하는 코드를 추가 하는 작업이 포함 됩니다. 이러한 작업은 특정 조건이 충족 될 때 사용자가 뷰를 선택 하거나 전환 하기 위해 새 메뉴 항목을 추가 하는 방법으로 수행할 수 있습니다.

새 메뉴 항목 및 명령 처리기 함수를 추가 하는 방법에 대 한 자세한 내용은 [명령 및 컨트롤 알림에 대 한 처리기](handlers-for-commands-and-control-notifications.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[문서/뷰 아키텍처](document-view-architecture.md)
