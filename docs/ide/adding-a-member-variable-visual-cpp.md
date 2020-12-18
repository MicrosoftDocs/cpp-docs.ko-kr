---
description: '자세한 정보: 멤버 변수 추가'
title: 멤버 변수 추가
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.member.variable
- vc.codewiz.variable.overview
helpviewer_keywords:
- member variables, adding
- member variables
- add member variable wizard [C++]
- dialog box controls, member variables
- dialog box controls, variable types
- variables, dialog box control member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
ms.openlocfilehash: b3af5c5920e465545623e9fa7239662954df2d66
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160118"
---
# <a name="add-a-member-variable"></a>멤버 변수 추가

클래스 뷰를 사용하여 클래스에 멤버 변수를 추가할 수 있습니다. 멤버 변수는 [데이터 교환 및 유효성 검사](../mfc/dialog-data-exchange-and-validation.md)용일 수도 있고 일반적일 수도 있습니다. 데이터 멤버 변수 마법사는 관련 정보를 가져와 적절한 위치에 있는 원본 파일에 요소를 삽입하는 데 사용하도록 설계되었습니다. [대화 상자 편집기](../windows/dialog-editor.md)의 [리소스 뷰](../windows/how-to-create-a-resource-script-file.md#create-resources) 또는 [클래스 뷰](/visualstudio/ide/viewing-the-structure-of-code)에서 멤버 변수를 추가할 수 있습니다.

> [!NOTE]
> 대화 상자를 디자인하고 구현할 때 대화 상자 편집기를 사용하여 대화 상자 컨트롤을 추가한 다음, 컨트롤의 멤버 변수를 구현하는 것이 더 효율적일 수 있습니다.

**멤버 변수 추가 마법사를 사용하여 리소스 뷰에서 대화 상자 컨트롤의 멤버 변수를 추가하려면:**

1. 리소스 뷰에서 프로젝트 노드와 대화 상자 노드를 확장하여 프로젝트의 대화 상자 목록을 표시합니다.

1. 멤버 변수를 추가할 대화 상자를 두 번 클릭하여 대화 상자 편집기에서 엽니다.

1. 대화 상자 편집기에 표시된 대화 상자에서 멤버 변수를 추가할 컨트롤을 마우스 오른쪽 단추로 클릭합니다.

1. 바로 가기 메뉴에서 **변수 추가** 를 선택하여 [멤버 변수 추가 마법사](#add-member-variable-wizard)를 표시합니다.

   > [!NOTE]
   > 기본값은 **컨트롤 ID** 에 이미 제공되어 있습니다.

1. 적절한 마법사 상자에 정보를 입력합니다. 자세한 내용은 [대화 상자 컨트롤 및 변수 형식](#dialog-box-controls-and-variable-types)을 참조하세요.

1. **마침** 을 선택하여 정의 및 구현 코드를 프로젝트에 추가하고 마법사를 닫습니다.

**멤버 변수 추가 마법사를 사용하여 클래스 뷰에서 멤버 변수를 추가하려면:**

1. [클래스 뷰](/visualstudio/ide/viewing-the-structure-of-code)에서 프로젝트 노드를 확장하여 프로젝트의 클래스를 표시합니다.

1. 변수를 추가할 클래스를 마우스 오른쪽 단추로 클릭합니다.

1. 바로 가기 메뉴에서 **추가** 를 선택한 다음, **변수 추가** 를 선택하여 멤버 변수 추가 마법사를 표시합니다.

1. 적절한 마법사 상자에 정보를 입력합니다. 자세한 내용은 [멤버 변수 추가 마법사](#add-member-variable-wizard)를 참조하세요.

1. **마침** 을 선택하여 정의 및 구현 코드를 프로젝트에 추가하고 마법사를 닫습니다.

## <a name="in-this-section"></a>단원 내용

- [멤버 변수 추가 마법사](#add-member-variable-wizard)
- [대화 상자 컨트롤 및 변수 형식](#dialog-box-controls-and-variable-types)

## <a name="add-member-variable-wizard"></a>멤버 변수 추가 마법사

이 마법사는 멤버 변수 선언을 헤더 파일에 추가합니다. 옵션에 따라 .cpp 파일에 코드를 추가할 수 있습니다. 마법사를 사용하여 멤버 변수를 추가하면 개발 환경에서 코드를 편집할 수 있습니다.

- **Access**

  멤버 변수에 대한 액세스를 설정합니다. 액세스 한정자는 다른 클래스가 멤버 변수에 포함되는 액세스를 지정하는 키워드입니다. 액세스 권한 지정에 대한 자세한 내용은 [멤버 액세스 제어](../cpp/member-access-control-cpp.md)를 참조하세요. 멤버 변수 액세스 수준은 기본적으로 **`public`** 으로 설정됩니다.

  - [public](../cpp/public-cpp.md)
  - [protected](../cpp/protected-cpp.md)
  - [private](../cpp/private-cpp.md)

- **변수 형식**

  추가하는 멤버 변수의 반환 형식을 설정합니다.

  - 대화 상자 컨트롤이 아닌 멤버 변수를 추가하는 경우 사용 가능한 형식 목록에서 선택합니다.

    형식에 대한 자세한 내용은 [기본 형식](../cpp/fundamental-types-cpp.md)을 참조하세요.

    - **`char`**
    - **`double`**
    - **`float`**
    - **`int`**
    - **`long`**
    - **`short`**
    - **`unsigned char`**
    - **`unsigned int`**
    - **`unsigned long`**

  - 대화 상자 컨트롤에 멤버 변수를 추가하는 경우 이 상자는 컨트롤이나 값에 대해 반환된 개체의 형식으로 채워집니다. **컨트롤** 을 선택하는 경우 **변수 형식** 은 **컨트롤 ID** 상자에서 선택한 컨트롤의 기본 클래스를 지정합니다. 대화 상자 컨트롤에 값이 포함될 수 있는 경우 및 **값** 을 선택한 경우 **변수 형식** 은 컨트롤이 포함할 수 있는 값에 적절한 형식을 지정합니다. 자세한 내용은 [대화 상자 컨트롤 및 변수 형식](#dialog-box-controls-and-variable-types)을 참조하세요.

    이 값은 **컨트롤 ID** 의 선택 영역에 따라 다르며 변경할 수 없습니다.

- **변수 이름**

  추가하는 멤버 변수의 이름을 설정합니다. 멤버 변수는 일반적으로 기본 제공되는 `m_` 식별 문자열로 시작합니다.

- **제어 변수**

  멤버 변수가 [데이터 교환 및 데이터 유효성](../mfc/dialog-data-exchange-and-validation.md) 지원을 사용하여 대화 상자 내에서 컨트롤을 관리한다고 표시합니다. 자세한 정보는 [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)를 참조하세요. 이 옵션은 [CDialog](../mfc/reference/cdialog-class.md)에서 파생된 클래스에 추가된 멤버 변수에 사용할 수 있습니다. **컨트롤 ID** 및 **컨트롤 형식** 옵션을 활성화하려면 이 상자를 선택합니다.

- **컨트롤 ID**

  추가하는 제어 변수의 ID를 설정합니다. 멤버 변수를 추가하는 컨트롤 형식의 ID를 목록에서 선택합니다. **제어 변수** 상자를 선택한 경우에만 목록이 활성화되고, 대화 상자에 이미 추가된 컨트롤의 ID로 제한됩니다. 예를 들어 표준 **확인** 단추에서 컨트롤 ID는 **IDOK** 입니다.

  |옵션|설명|
  |------------|-----------------|
  |**컨트롤**|이 옵션은 컨트롤 형식에 대해 기본적으로 설정되며, 목록 상자, 콤보 상자 또는 편집 상자에서 관리하려고 할 수 있으므로 컨트롤의 상태나 콘텐츠가 아닌 컨트롤 자체를 관리합니다.|
  |**값**|이 옵션은 편집 상자나 확인란 등 값을 포함하거나 상태를 표시할 수 있는 컨트롤 형식에 사용할 수 있습니다. 범위, 콘텐츠 또는 상태를 관리할 수 있는 컨트롤 형식에 사용할 수도 있습니다. 자세한 내용은 [대화 상자 컨트롤 및 변수 형식](#dialog-box-controls-and-variable-types)을 참조하세요.|

- **범주**

  변수가 컨트롤 형식과 컨트롤 값 중 어느 것을 기반으로 하는지 지정합니다.

- **컨트롤 형식**

  추가되는 컨트롤의 형식을 설정합니다. 이 상자는 변경할 수 없습니다. 예를 들어 단추에 컨트롤 형식 **BUTTON** 가 있고, 콤보 상자에 컨트롤 형식 **COMBOBOX** 가 있습니다. 자세한 내용은 [대화 상자 컨트롤 및 변수 형식](#dialog-box-controls-and-variable-types)을 참조하세요.

- **최대 문자**

  **변수 형식** 이 [CString](../atl-mfc-shared/reference/cstringt-class.md)으로 설정된 경우에만 사용할 수 있습니다. 컨트롤이 포함할 수 있는 문자의 최대 수를 나타냅니다.

- **최소값**

  변수 형식이 `BOOL`, **`int`** , `UINT`, **`long`** , `DWORD`, **`float`** , **`double`** , `BYTE`, **`short`** , [COLECurrency](../mfc/reference/colecurrency-class.md) 또는 [CTime](../atl-mfc-shared/reference/ctime-class.md)인 경우에만 사용할 수 있습니다. 소수 자릿수 또는 날짜 범위에 허용되는 가장 낮은 값을 나타냅니다.

- **최대값**

  변수 형식이 `BOOL`, **`int`** , `UINT`, **`long`** , `DWORD`, **`float`** , **`double`** , `BYTE`, **`short`** , `COLECurrency` 또는 `CTime`인 경우에만 사용할 수 있습니다. 소수 자릿수 또는 날짜 범위에 허용되는 가장 높은 값을 나타냅니다.

- **.h 파일**

  ActiveX 컨트롤의 경우 해당 멤버 변수에는 래퍼 클래스가 필요합니다. 클래스 선언에 추가할 헤더 파일의 이름을 설정합니다.

- **.cpp 파일**

  ActiveX 컨트롤의 경우 해당 멤버 변수에는 래퍼 클래스가 필요합니다. 클래스 정의에 추가할 구현 파일의 이름을 설정합니다.

- **설명**

  멤버 변수에 대한 헤더 파일에 주석을 제공합니다.

## <a name="dialog-box-controls-and-variable-types"></a>대화 상자 컨트롤 및 변수 형식

MFC를 사용하여 만든 대화 상자 컨트롤에 멤버 변수를 추가하는 데 [멤버 변수 추가 마법사](#add-member-variable-wizard)를 사용할 수 있습니다. 멤버 변수를 추가하는 컨트롤의 형식은 대화 상자에 표시되는 옵션을 결정합니다.

다음 표에서는 MFC에서 지원되는 모든 대화 상자 컨트롤 형식 및 [대화 상자 편집기](../windows/dialog-editor.md)에 대해 설명합니다. 사용 가능한 형식 및 값도 표시합니다.

|컨트롤|컨트롤 형식|제어 변수 형식|변수 값 형식|최소값/최대값(값 형식에만 해당)|
|-------------|------------------|---------------------------|-------------------------|-----------------------------------------|
|애니메이션 컨트롤|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|없음; 컨트롤에만 해당|N/A|
|단추|BUTTON|[CButton](../mfc/reference/cbutton-class.md)|없음; 컨트롤에만 해당|N/A|
|확인란|CHECK|[CButton](../mfc/reference/cbutton-class.md)|`BOOL`|최소값/최대값|
|콤보 상자|COMBOBOX|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString](../atl-mfc-shared/reference/cstringt-class.md)|최대 문자|
|날짜 시간 선택 컨트롤|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[CTime](../atl-mfc-shared/reference/ctime-class.md)|최소값/최대값|
|편집 상자|편집|[CEdit](../mfc/reference/cedit-class.md)|`CString`, int, UINT, long, DWORD, float, double, BYTE, short, BOOL, `COleDateTime` 또는 `COleCurrency`|최소값/최대값; 일부 지원 최대 문자|
|바로 가기 키 컨트롤|msctls_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|없음; 컨트롤에만 해당|N/A|
|목록 상자|LISTBOX|[CListBox](../mfc/reference/clistbox-class.md)|`CString`|최대 문자|
|목록 컨트롤|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|없음; 컨트롤에만 해당|N/A|
|MonthCalendar 컨트롤|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|최소값/최대값|
|Progress 컨트롤|msctls_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|없음; 컨트롤에만 해당|N/A|
|Rich Edit 2 컨트롤|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|최대 문자|
|Rich Edit 컨트롤|RICHEDIT|`CRichEditCtrl`|`CString`|최대 문자|
|스크롤 막대(가로 또는 세로)|SCROLLBAR|[CScrollBar](../mfc/reference/cscrollbar-class.md)|**`int`**|최소값/최대값|
|Slider 컨트롤|msctls_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|**`int`**|최소값/최대값|
|Spin 컨트롤|msctls_updown32|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|없음; 컨트롤에만 해당|N/A|
|탭 컨트롤|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|없음; 컨트롤에만 해당|N/A|
|트리 컨트롤|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|없음; 컨트롤에만 해당|N/A|
