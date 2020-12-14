---
description: '자세한 정보: ActiveX 컨트롤 컨테이너: activex 컨트롤 컨테이너에서 ActiveX 컨트롤 프로그래밍'
title: 'ActiveX 컨트롤 컨테이너: ActiveX 컨트롤 컨테이너에서 ActiveX 컨트롤 프로그래밍'
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- Confirm Classes dialog box
- wrapper classes [MFC], ActiveX controls
- ActiveX control containers [MFC], wrapper classes
- ActiveX controls [MFC], accessing
- MFC ActiveX controls [MFC], accessing in containers
- header files [MFC], for ActiveX control wrapper class
- wrapper classes [MFC], using
- ActiveX controls [MFC], wrapper classes
ms.assetid: ef9b2480-92d6-4191-b16e-8055c4fd7b73
ms.openlocfilehash: 34a5a2aaa1d7ec940ea31ae2fbe8c89ba3d84818
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251013"
---
# <a name="activex-control-containers-programming-activex-controls-in-an-activex-control-container"></a>ActiveX 컨트롤 컨테이너: ActiveX 컨트롤 컨테이너에서 ActiveX 컨트롤 프로그래밍

이 문서에서는 포함 된 ActiveX 컨트롤의 노출 된 [메서드](../mfc/mfc-activex-controls-methods.md) 및 [속성](../mfc/mfc-activex-controls-properties.md) 에 액세스 하는 프로세스에 대해 설명 합니다.

>[!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. ActiveX를 대체 하는 최신 기술에 대 한 자세한 내용은 [Activex Controls](activex-controls.md)을 참조 하세요.

기본적으로 다음 단계를 수행 합니다.

1. 갤러리를 사용 하 여 activex [컨트롤을 activex 컨테이너 프로젝트에 삽입](../mfc/inserting-a-control-into-a-control-container-application.md) 합니다.

1. ActiveX 컨트롤 래퍼 클래스와 동일한 형식의 멤버 변수 (또는 다른 형식의 액세스) [를 정의](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) 합니다.

1. 래퍼 클래스의 미리 정의 된 멤버 함수를 사용 하 여 [ActiveX 컨트롤을 프로그래밍](#_core_programming_the_activex_control) 합니다.

이 토론에서는 ActiveX 컨트롤을 지 원하는 대화 상자 기반 프로젝트 (명명 된 컨테이너)를 만들었다고 가정 합니다. Circ 샘플 컨트롤인 Circ가 결과 프로젝트에 추가 됩니다.

프로젝트에 Circ 컨트롤이 삽입 되 면 (1 단계) 응용 프로그램의 주 대화 상자에 Circ 컨트롤의 인스턴스를 삽입 합니다.

## <a name="procedures"></a>프로시저

#### <a name="to-add-the-circ-control-to-the-dialog-template"></a>대화 상자 템플릿에 Circ 컨트롤을 추가 하려면

1. ActiveX 컨트롤 컨테이너 프로젝트를 로드 합니다. 이 예제에서는 프로젝트를 사용 `Container` 합니다.

1. 리소스 뷰 탭을 클릭 합니다.

1. **대화 상자** 폴더를 엽니다.

1. 주 대화 상자 템플릿을 두 번 클릭 합니다. 이 예에서는 **IDD_CONTAINER_DIALOG** 을 사용 합니다.

1. 도구 상자에서 Circ 컨트롤 아이콘을 클릭 합니다.

1. 대화 상자 내에서 한 지점을 클릭 하 여 Circ 컨트롤을 삽입 합니다.

1. **파일** 메뉴에서 **모두 저장** 을 선택 하 여 대화 상자 템플릿의 모든 수정 내용을 저장 합니다.

## <a name="modifications-to-the-project"></a>프로젝트 수정

컨테이너 응용 프로그램에서 Circ 컨트롤에 액세스할 수 있도록 Visual C++ 래퍼 클래스 ( `CCirc` ) 구현 파일 ()을 자동으로 추가 합니다. CPP)를 컨테이너 프로젝트와 래퍼 클래스 헤더 (. H) 파일을 대화 상자 헤더 파일로:

[!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_1.h)]

## <a name="the-wrapper-class-header-h-file"></a><a name="_core_the_wrapper_class_header_28h29_file"></a> 래퍼 클래스 헤더 (. H) 파일

래퍼 클래스는 Circ 컨트롤에 대 한 속성 (및 호출 메서드)을 가져오고 설정 하기 위해 `CCirc` 모든 노출 된 메서드 및 속성의 선언을 제공 합니다. 이 예제에서 이러한 선언은 CIRC. H에서 찾을 수 있습니다. 다음 샘플은 `CCirc` ActiveX 컨트롤의 노출 된 인터페이스를 정의 하는 클래스의 일부입니다.

[!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_2.h)]
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_3.h)]

그런 다음 일반 c + + 구문을 사용 하 여 응용 프로그램의 다른 프로시저에서 이러한 함수를 호출할 수 있습니다. 이 멤버 함수 집합을 사용 하 여 컨트롤의 메서드 및 속성에 액세스 하는 방법에 대 한 자세한 내용은 [ActiveX 컨트롤 프로그래밍](#_core_programming_the_activex_control)단원을 참조 하십시오.

## <a name="member-variable-modifications-to-the-project"></a><a name="_core_member_variable_modifications_to_the_project"></a> 프로젝트에 대 한 멤버 변수 수정

ActiveX 컨트롤이 프로젝트에 추가 되 고 대화 상자 컨테이너에 포함 되 면 프로젝트의 다른 부분에서 액세스할 수 있습니다. 컨트롤에 액세스 하는 가장 쉬운 방법은 [](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) `CContainerDlg` Visual C++ 하 여 프로젝트에 추가 된 래퍼 클래스와 동일한 형식의 대화 상자 클래스 (2 단계)의 멤버 변수를 만드는 것입니다. 그런 다음 멤버 변수를 사용 하 여 언제 든 지 포함 된 컨트롤에 액세스할 수 있습니다.

**멤버 변수 추가** 대화 상자에서 프로젝트에 *m_circctl* 멤버 변수를 추가 하면 헤더 파일 ()에도 다음 줄이 추가 됩니다. H) `CContainerDlg` 클래스:

[!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_4.h)]
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_5.h)]

또한 **DDX_Control** 호출은의 구현에 자동으로 추가 됩니다 `CContainerDlg` `DoDataExchange` .

[!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_6.cpp)]

## <a name="programming-the-activex-control"></a><a name="_core_programming_the_activex_control"></a> ActiveX 컨트롤 프로그래밍

이 시점에서 ActiveX 컨트롤을 대화 상자 템플릿에 삽입 하 고이에 대 한 멤버 변수를 만들었습니다. 이제 공용 c + + 구문을 사용 하 여 포함 된 컨트롤의 속성 및 메서드에 액세스할 수 있습니다.

설명 된 대로 ( [래퍼 클래스 헤더 (. H) 파일](#_core_the_wrapper_class_header_28h29_file)), 헤더 파일 (. H)의 `CCirc` 래퍼 클래스 (이 경우에는 CIRC) H에는 노출 된 속성 값을 가져오고 설정 하는 데 사용할 수 있는 멤버 함수 목록이 포함 되어 있습니다. 노출 된 메서드에 대 한 멤버 함수도 사용할 수 있습니다.

컨트롤의 속성을 수정 하는 일반적인 장소는 `OnInitDialog` 주 대화 상자 클래스의 멤버 함수에 있습니다. 이 함수는 대화 상자가 표시 되기 직전에 호출 되며 컨트롤을 포함 하 여 콘텐츠를 초기화 하는 데 사용 됩니다.

다음 코드 예제에서는 *m_circctl* 멤버 변수를 사용 하 여 포함 된 Circ 컨트롤의 Caption 및 CircleShape 속성을 수정 합니다.

[!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_7.cpp)]

## <a name="see-also"></a>참고 항목

[ActiveX 컨트롤 컨테이너](../mfc/activex-control-containers.md)
