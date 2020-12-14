---
description: '자세한 정보: MFC ActiveX 컨트롤: 고급 항목'
title: 'MFC ActiveX 컨트롤: 고급 항목'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- MFC ActiveX controls [MFC], accessing invisible dialog controls
- MFC ActiveX controls [MFC], advanced topics
- FireError method [MFC]
- MFC ActiveX controls [MFC], database classes
- MFC ActiveX controls [MFC], special keys
- PreTranslateMessage method [MFC]
- MFC ActiveX controls [MFC], parameterized property
- ThrowError method [MFC]
ms.assetid: e9e34abb-8e2d-461e-bb9c-a1aec5dcecbd
ms.openlocfilehash: 1b37c3621c515153f068633b8272420a68a06c4e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280744"
---
# <a name="mfc-activex-controls-advanced-topics"></a>MFC ActiveX 컨트롤: 고급 항목

이 문서에서는 ActiveX 컨트롤 개발과 관련 된 고급 항목을 다룹니다. 여기에는 다음이 포함됩니다.

- [ActiveX 컨트롤에서 데이터베이스 클래스 사용](#_core_using_database_classes_in_activex_controls)

- [매개 변수가 있는 속성 구현](#_core_implementing_a_parameterized_property)

- [ActiveX 컨트롤의 오류 처리](#_core_handling_errors_in_your_activex_control)

- [컨트롤에서 특수 키 처리](#_core_handling_special_keys_in_your_control)

- [런타임에 보이지 않는 대화 상자 컨트롤 액세스](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)

>[!IMPORTANT]
> ActiveX는 새로운 개발에 사용 하지 않아야 하는 레거시 기술입니다. ActiveX를 대체 하는 최신 기술에 대 한 자세한 내용은 [Activex Controls](activex-controls.md)을 참조 하세요.

## <a name="using-database-classes-in-activex-controls"></a><a name="_core_using_database_classes_in_activex_controls"></a> ActiveX 컨트롤에서 데이터베이스 클래스 사용

ActiveX 컨트롤 클래스는 클래스 라이브러리의 일부 이므로 표준 MFC 응용 프로그램에서 데이터베이스 클래스를 사용 하 여 MFC 데이터베이스 클래스를 사용 하는 ActiveX 컨트롤을 개발 하는 데 동일한 프로시저와 규칙을 적용할 수 있습니다.

MFC 데이터베이스 클래스에 대 한 일반적인 개요는 [Mfc 데이터베이스 클래스 (DAO 및 ODBC)](../data/mfc-database-classes-odbc-and-dao.md)를 참조 하세요. 이 문서에서는 MFC ODBC 클래스와 MFC DAO 클래스를 모두 소개 하 고 이러한 클래스에 대해 자세히 설명 합니다.

> [!NOTE]
> DAO는 Office 2013을 통해 지원 됩니다. DAO 3.6은 최종 버전이 며 사용 되지 않는 것으로 간주 됩니다. Visual C++ 환경과 마법사는 dao를 지원 하지 않습니다 (DAO 클래스가 포함 되어 있지만 계속 사용할 수 있음). 새 프로젝트에 [OLE DB 템플릿](../data/oledb/ole-db-programming.md) 또는 [ODBC 및 MFC](../data/odbc/odbc-and-mfc.md) 를 사용 하는 것이 좋습니다. DAO는 기존 응용 프로그램을 유지 관리 하는 데만 사용 해야 합니다.

## <a name="implementing-a-parameterized-property"></a><a name="_core_implementing_a_parameterized_property"></a> 매개 변수가 있는 속성 구현

매개 변수가 있는 속성 (속성 배열 이라고 함)은 값의 동일 컬렉션을 컨트롤의 단일 속성으로 노출 하기 위한 메서드입니다. 예를 들어 매개 변수가 있는 속성을 사용 하 여 배열 또는 사전을 속성으로 노출할 수 있습니다. Visual Basic에서 이러한 속성은 배열 표기법을 사용 하 여 액세스 됩니다.

[!code-vb[NVC_MFC_AxVb#1](codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]

속성 추가 마법사를 사용 하 여 매개 변수가 있는 속성을 구현 합니다. 속성 추가 마법사는 컨트롤 사용자가 위의 표기법 또는 표준 방식으로 속성에 액세스할 수 있도록 하는 Get/Set 함수 쌍을 추가 하 여 속성을 구현 합니다.

메서드 및 속성과 마찬가지로 매개 변수가 있는 속성도 허용 되는 매개 변수 수에 제한이 있습니다. 매개 변수가 있는 속성의 경우 15 개 매개 변수 (속성 값을 저장 하기 위해 예약 된 매개 변수 하나)입니다.

다음 절차에서는 배열 이라는 매개 변수가 있는 속성을 추가 합니다 .이 속성은 정수의 2 차원 배열로 액세스할 수 있습니다.

#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>속성 추가 마법사를 사용 하 여 매개 변수가 있는 속성을 추가 하려면

1. 컨트롤의 프로젝트를 로드합니다.

1. 클래스 뷰에서 컨트롤의 라이브러리 노드를 확장합니다.

1. 컨트롤의 인터페이스 노드(라이브러리 노드의 두 번째 노드)를 마우스 오른쪽 단추로 클릭하여 바로 가기 메뉴를 엽니다.

1. 바로 가기 메뉴에서 **추가** 를 클릭 한 다음 **속성 추가** 를 클릭 합니다.

1. **속성 이름** 상자에을 입력 `Array` 합니다.

1. **속성 유형** 상자에서를 선택 **`short`** 합니다.

1. **구현** 형식에서 **Get/Set 메서드** 를 클릭 합니다.

1. **Get function** And **set Function** 상자에 get 및 set 함수의 고유 이름을 입력 하거나 기본 이름을 적용 합니다.

1. 매개 변수 **이름** 및 **매개 변수 형식** 컨트롤을 사용 하 여 *행* ( *short* 형식) 이라는 매개 변수를 추가 합니다.

1. *열* ( *short* 형식) 이라는 두 번째 매개 변수를 추가 합니다.

1. **Finish** 를 클릭합니다.

### <a name="changes-made-by-the-add-property-wizard"></a>속성 추가 마법사에서 변경한 내용

사용자 지정 속성을 추가 하면 속성 추가 마법사가 컨트롤 클래스 헤더를 변경 합니다 (. H) 및 구현 (. CPP) 파일.

다음 줄이 컨트롤 클래스에 추가 됩니다. H 파일 (H):

[!code-cpp[NVC_MFC_AxUI#35](codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]

이 코드는 `GetArray` `SetArray` 사용자가 속성에 액세스할 때 특정 행과 열을 요청할 수 있도록 하는 및 라는 두 개의 함수를 선언 합니다.

또한 속성 추가 마법사는 컨트롤 클래스 구현 ()에 있는 컨트롤 디스패치 맵에 다음 줄을 추가 합니다. CPP) 파일:

[!code-cpp[NVC_MFC_AxUI#36](codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]

마지막으로 및 함수의 구현이의 `GetArray` `SetArray` 끝에 추가 됩니다. CPP 파일. 대부분의 경우 Get 함수를 수정 하 여 속성의 값을 반환 합니다. Set 함수는 일반적으로 속성이 변경 되기 전이나 후에 실행 해야 하는 코드를 포함 합니다.

이 속성이 유용 하려면 형식의 컨트롤 클래스에서 2 차원 배열 멤버 변수를 선언 **`short`** 하 여 매개 변수가 있는 속성에 대 한 값을 저장할 수 있습니다. 그런 다음 매개 변수에 표시 된 대로 적절 한 행 및 열에 저장 된 값을 반환 하도록 Get 함수를 수정 하 고 Set 함수를 수정 하 여 행 및 열 매개 변수에서 참조 하는 값을 업데이트할 수 있습니다.

## <a name="handling-errors-in-your-activex-control"></a><a name="_core_handling_errors_in_your_activex_control"></a> ActiveX 컨트롤의 오류 처리

컨트롤에서 오류 조건이 발생 하는 경우 컨트롤 컨테이너에 오류를 보고 해야 할 수 있습니다. 오류가 발생 하는 상황에 따라 오류를 보고 하는 방법에는 두 가지가 있습니다. 오류가 속성의 Get 또는 Set 함수 내에서 발생 하거나 OLE 자동화 메서드 구현 내에서 발생 하는 경우 컨트롤은 [COleControl:: ThrowError](reference/colecontrol-class.md#throwerror)를 호출 하 여 오류가 발생 했음을 컨트롤 사용자에 게 알립니다. 오류가 다른 시간에 발생 하는 경우 컨트롤은 스톡 오류 이벤트를 발생 시키는 [COleControl:: FireError](reference/colecontrol-class.md#fireerror)를 호출 해야 합니다.

발생 한 오류의 종류를 나타내려면 컨트롤이 또는에 오류 코드를 전달 해야 합니다 `ThrowError` `FireError` . 오류 코드는 32 비트 값을 포함 하는 OLE 상태 코드입니다. 가능 하면 OLECTL에 정의 된 표준 코드 집합에서 오류 코드를 선택 합니다. H 헤더 파일입니다. 다음 표에서는 이러한 코드를 요약 합니다.

### <a name="activex-control-error-codes"></a>ActiveX 컨트롤 오류 코드

|오류|설명|
|-----------|-----------------|
|CTL_E_ILLEGALFUNCTIONCALL|함수 호출이 잘못 되었습니다.|
|CTL_E_OVERFLOW|오버플로|
|CTL_E_OUTOFMEMORY|메모리가 부족합니다.|
|CTL_E_DIVISIONBYZERO|0으로 나누었습니다.|
|CTL_E_OUTOFSTRINGSPACE|문자열 공간이 부족합니다.|
|CTL_E_OUTOFSTACKSPACE|스택 공간이 부족합니다.|
|CTL_E_BADFILENAMEORNUMBER|파일 이름 또는 번호가 잘못되었습니다.|
|CTL_E_FILENOTFOUND|파일을 찾을 수 없음|
|CTL_E_BADFILEMODE|파일 모드가 잘못되었습니다.|
|CTL_E_FILEALREADYOPEN|파일이 이미 열려 있습니다.|
|CTL_E_DEVICEIOERROR|디바이스 입/출력(I/O) 오류입니다.|
|CTL_E_FILEALREADYEXISTS|파일이 이미 있습니다.|
|CTL_E_BADRECORDLENGTH|레코드 길이가 잘못되었습니다.|
|CTL_E_DISKFULL|디스크가 꽉 참|
|CTL_E_BADRECORDNUMBER|레코드 개수가 잘못되었습니다.|
|CTL_E_BADFILENAME|파일 이름이 잘못 되었습니다.|
|CTL_E_TOOMANYFILES|파일이 너무 많습니다.|
|CTL_E_DEVICEUNAVAILABLE|디바이스를 사용할 수 없습니다.|
|CTL_E_PERMISSIONDENIED|사용 권한이 거부됨|
|CTL_E_DISKNOTREADY|디스크가 준비되지 않았습니다.|
|CTL_E_PATHFILEACCESSERROR|경로/파일 액세스 오류|
|CTL_E_PATHNOTFOUND|경로를 찾을 수 없습니다.|
|CTL_E_INVALIDPATTERNSTRING|잘못된 패턴 문자열|
|CTL_E_INVALIDUSEOFNULL|NULL 사용이 잘못 되었습니다.|
|CTL_E_INVALIDFILEFORMAT|파일 형식이 잘못 되었습니다.|
|CTL_E_INVALIDPROPERTYVALUE|잘못 된 속성 값|
|CTL_E_INVALIDPROPERTYARRAYINDEX|속성 배열 인덱스가 잘못 되었습니다.|
|CTL_E_SETNOTSUPPORTEDATRUNTIME|Set은 런타임에 지원되지 않습니다.|
|CTL_E_SETNOTSUPPORTED|Set은 지원되지 않습니다(읽기 전용 속성).|
|CTL_E_NEEDPROPERTYARRAYINDEX|속성 배열 인덱스가 필요합니다.|
|CTL_E_SETNOTPERMITTED|Set은 허용되지 않습니다.|
|CTL_E_GETNOTSUPPORTEDATRUNTIME|Get은 런타임에 지원되지 않습니다.|
|CTL_E_GETNOTSUPPORTED|Get은 지원되지 않습니다(쓰기 전용 속성).|
|CTL_E_PROPERTYNOTFOUND|속성을 찾을 수 없습니다.|
|CTL_E_INVALIDCLIPBOARDFORMAT|클립보드 형식이 잘못 되었습니다.|
|CTL_E_INVALIDPICTURE|잘못 된 그림|
|CTL_E_PRINTERERROR|프린터 오류|
|CTL_E_CANTSAVEFILETOTEMP|TEMP에 파일을 저장할 수 없습니다.|
|CTL_E_SEARCHTEXTNOTFOUND|검색 텍스트를 찾을 수 없습니다.|
|CTL_E_REPLACEMENTSTOOLONG|대체 텍스트가 너무 깁니다.|

필요한 경우 CUSTOM_CTL_SCODE 매크로를 사용 하 여 표준 코드 중 하나에 포함 되지 않은 조건에 대 한 사용자 지정 오류 코드를 정의 합니다. 이 매크로에 대 한 매개 변수는 1000 및 32767 (포함) 사이의 정수 여야 합니다. 예를 들어:

[!code-cpp[NVC_MFC_AxUI#37](codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]

ActiveX 컨트롤을 만들어 기존 VBX 컨트롤을 바꾸려면 VBX 컨트롤이 사용 하는 것과 동일한 숫자 값으로 ActiveX 컨트롤 오류 코드를 정의 하 여 오류 코드가 호환 되는지 확인 합니다.

## <a name="handling-special-keys-in-the-control"></a><a name="_core_handling_special_keys_in_your_control"></a> 컨트롤에서 특수 키 처리

경우에 따라 특정 한 키 입력 조합을 특수 한 방식으로 처리 하는 것이 좋습니다. 예를 들어 여러 줄 텍스트 상자 컨트롤에서 ENTER 키를 누를 때 새 줄을 삽입 하거나 방향 키 ID를 누를 때 편집 컨트롤 그룹 간을 이동 합니다.

ActiveX 컨트롤의 기본 클래스가 이면 `COleControl` [CWnd::P retranslatemessage](reference/cwnd-class.md#pretranslatemessage) 를 재정의 하 여 컨테이너에서 처리 하기 전에 메시지를 처리할 수 있습니다. 이 기술을 사용 하는 경우의 재정의에서 메시지를 처리 하는 경우 항상 **TRUE** 를 반환 `PreTranslateMessage` 합니다.

다음 코드 예제에서는 방향 키와 관련 된 모든 메시지를 처리할 수 있는 방법을 보여 줍니다.

[!code-cpp[NVC_MFC_AxUI#38](codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]

ActiveX 컨트롤에 대 한 키보드 인터페이스를 처리 하는 방법에 대 한 자세한 내용은 ActiveX SDK 설명서를 참조 하십시오.

## <a name="accessing-dialog-controls-that-are-invisible-at-run-time"></a><a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a> 런타임에 보이지 않는 대화 상자 컨트롤 액세스

사용자 인터페이스가 없고 런타임에 표시 되지 않는 대화 상자 컨트롤을 만들 수 있습니다. 숨겨진 런타임에 ActiveX 컨트롤을 대화 상자에 추가 하 고 [CWnd:: GetDlgItem](reference/cwnd-class.md#getdlgitem) 를 사용 하 여 컨트롤에 액세스 하는 경우 컨트롤이 제대로 작동 하지 않습니다. 대신, 다음 방법 중 하나를 사용 하 여 컨트롤을 나타내는 개체를 가져와야 합니다.

- 멤버 변수 추가 마법사를 사용 하 여 **제어 변수** 를 선택한 다음 컨트롤의 ID를 선택 합니다. 멤버 변수 이름을 입력 하 고 컨트롤의 래퍼 클래스를 **컨트롤 형식** 으로 선택 합니다.

     또는

- 로컬 변수와 하위 클래스를 대화 상자 항목으로 선언 합니다. 다음과 유사한 코드를 삽입 합니다 ( `CMyCtrl` 는 래퍼 클래스이 고, IDC_MYCTRL1는 컨트롤의 ID).

   [!code-cpp[NVC_MFC_AxCont#19](codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)
