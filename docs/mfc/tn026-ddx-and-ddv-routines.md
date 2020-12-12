---
description: 'TN026: DDX 및 DDV 루틴에 대해 자세히 알아보세요.'
title: 'TN026: DDX 및 DDV 루틴'
ms.date: 06/28/2018
f1_keywords:
- DDX
- DDV
helpviewer_keywords:
- DDX (dialog data exchange), procedures
- TN026
- DDV (dialog data validation), procedures
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
ms.openlocfilehash: 1e5c8d3679b7e91ad7f356c1e6f6badc61cdd46f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215705"
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026: DDX 및 DDV 루틴

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

이 참고에서는 DDX (대화 상자 데이터 교환) 및 DDV (대화 상자 데이터 유효성 검사) 아키텍처에 대해 설명 합니다. 또한 DDX_ 또는 DDV_ 프로시저를 작성 하는 방법과 루틴을 사용 하도록 클래스 마법사를 확장 하는 방법을 설명 합니다.

## <a name="overview-of-dialog-data-exchange"></a>대화 상자 데이터 교환 개요

모든 대화 상자 데이터 함수는 c + + 코드를 사용 하 여 수행 됩니다. 특수 리소스 또는 매직 매크로가 없습니다. 메커니즘의 핵심은 대화 상자 데이터 교환 및 유효성 검사를 수행 하는 모든 대화 상자 클래스에서 재정의 되는 가상 함수입니다. 항상 다음 형식으로 되어 있습니다.

```cpp
void CMyDialog::DoDataExchange(CDataExchange* pDX)
{
    CDialog::DoDataExchange(pDX);   // call base class

    //{{AFX_DATA_MAP(CMyDialog)
        <data_exchange_function_call>
        <data_validation_function_call>
    //}}AFX_DATA_MAP
}
```

특수 형식 AFX 주석은 클래스 마법사가이 함수 내에서 코드를 찾고 편집할 수 있도록 합니다. 클래스 마법사와 호환 되지 않는 코드는 특수 형식 주석 외부에 배치 해야 합니다.

위의 예제에서 \<data_exchange_function_call> 는 형식입니다.

```cpp
DDX_Custom(pDX, nIDC, field);
```

및 \<data_validation_function_call> 는 선택 사항이 며 다음과 같은 형식입니다.

```cpp
DDV_Custom(pDX, field, ...);
```

각 함수에 DDX_/DDV_ 쌍이 둘 이상 포함 될 수 있습니다 `DoDataExchange` .

MFC와 함께 제공 되는 모든 대화 상자 데이터 교환 루틴 및 대화 상자 데이터 유효성 검사 루틴 목록은 ' afxdd_. h '를 참조 하십시오.

대화 상자 데이터는 클래스의 멤버 데이터 뿐입니다 `CMyDialog` . 구조체 또는 이와 유사한 항목으로 저장 되지 않습니다.

## <a name="notes"></a>참고

이 "대화 상자 데이터"를 호출 하지만 모든 기능은에서 파생 된 모든 클래스에서 사용할 수 `CWnd` 있으며 대화 상자에만 국한 되지 않습니다.

데이터의 초기 값은 일반적으로 및 주석이 있는 블록에서 표준 c + + 생성자에 설정 됩니다 `//{{AFX_DATA_INIT` `//}}AFX_DATA_INIT` .

`CWnd::UpdateData` 는에 대 한 호출에 대 한 초기화 및 오류 처리를 수행 하는 작업입니다 `DoDataExchange` .

언제 `CWnd::UpdateData` 든 지를 호출 하 여 데이터 교환 및 유효성 검사를 수행할 수 있습니다. 기본적으로 `UpdateData` (TRUE)는 기본 처리기에서 호출 되 `CDialog::OnOK` 고 `UpdateData` (FALSE)는 기본값에서 호출 됩니다 `CDialog::OnInitDialog` .

DDV_ 루틴은 해당 *필드* 에 대 한 DDX_ 루틴 바로 뒤에와 야 합니다.

## <a name="how-does-it-work"></a>작동 방식

대화 상자 데이터를 사용 하기 위해 다음 사항을 이해할 필요는 없습니다. 그러나이를 백그라운드에서 작동 하는 방식을 이해 하면 사용자 고유의 exchange 또는 유효성 검사 프로시저를 작성 하는 데 도움이 됩니다.

`DoDataExchange`멤버 함수는 멤버 함수와 매우 유사 합니다. 즉, `Serialize` 클래스의 외부 형식 (이 경우 대화 상자의 컨트롤)에서/로 데이터를 가져오거나 설정 해야 합니다. *PDX* 매개 변수는 데이터 교환을 수행 하기 위한 컨텍스트입니다 `CArchive` .의 매개 변수와 비슷합니다 `CObject::Serialize` . *PDX* (개체)에는 방향 플래그를 포함 하는 `CDataExchange` 것과 같은 방향 플래그가 있습니다 `CArchive` .

- 인 경우 `!m_bSaveAndValidate` 컨트롤에 데이터 상태를 로드 합니다.

- 인 경우 `m_bSaveAndValidate` 컨트롤에서 데이터 상태를 설정 합니다.

유효성 검사 `m_bSaveAndValidate` 는가 설정 된 경우에만 발생 합니다. 의 값은 `m_bSaveAndValidate` 에 대 한 BOOL 매개 변수에 의해 결정 됩니다 `CWnd::UpdateData` .

세 가지 다른 흥미로운 `CDataExchange` 멤버가 있습니다.

- `m_pDlgWnd`: 컨트롤을 포함 하는 창 (일반적으로 대화 상자)입니다. 이는 DDX_ 호출자가 DDV_ 전역 함수가 모든 DDX/DDV 루틴에 ' t r u e '를 전달할 필요가 없도록 하는 것입니다.

- `PrepareCtrl`, 및 `PrepareEditCtrl` : 데이터 교환에 대 한 대화 상자 컨트롤을 준비 합니다. 유효성 검사에 실패 하는 경우 포커스를 설정 하기 위해 해당 컨트롤의 핸들을 저장 합니다. `PrepareCtrl` 는 편집이 아닌 컨트롤에 사용 되며 `PrepareEditCtrl` 편집 컨트롤에 사용 됩니다.

- `Fail`: 사용자에 게 입력 오류를 경고 하는 메시지 상자를 가져온 후에 호출 됩니다. 이 루틴은 마지막 컨트롤 (또는에 대 한 마지막 호출)에 포커스를 복원 `PrepareCtrl` `PrepareEditCtrl` 하 고 예외를 throw 합니다. 이 멤버 함수는 DDX_ 및 DDV_ 루틴 모두에서 호출 될 수 있습니다.

## <a name="user-extensions"></a>사용자 확장

기본 DDX/DDV 메커니즘을 확장 하는 방법에는 여러 가지가 있습니다. 다음과 같습니다.

- 새 데이터 형식을 추가 합니다.

    ```cpp
    CTime
    ```

- 새 exchange 프로시저 (DDX_)를 추가 합니다.

    ```cpp
    void PASCAL DDX_Time(CDataExchange* pDX, int nIDC, CTime& tm);
    ```

- 새 유효성 검사 프로시저 (DDV_)를 추가 합니다.

    ```cpp
    void PASCAL DDV_TimeFuture(CDataExchange* pDX, CTime tm, BOOL bFuture);
    // make sure time is in the future or past
    ```

- 임의의 식을 유효성 검사 프로시저에 전달 합니다.

    ```cpp
    DDV_MinMax(pDX, age, 0, m_maxAge);
    ```

    > [!NOTE]
    > 이러한 임의 식은 클래스 마법사에서 편집할 수 없으므로 특수 형식 주석 (//{{AFX_DATA_MAP (CMyClass)) 외부로 이동 해야 합니다.

`DoDialogExchange`멤버 함수에는 결합 된 exchange 및 유효성 검사 함수 호출을 사용 하는 다른 유효한 c + + 문과 조건 또는 조건이 있습니다.

```cpp
//{{AFX_DATA_MAP(CMyClass)
DDX_Check(pDX, IDC_SEX, m_bFemale);
DDX_Text(pDX, IDC_EDIT1, m_age);
//}}AFX_DATA_MAP
if (m_bFemale)
    DDV_MinMax(pDX, age, 0, m_maxFemaleAge);
else
    DDV_MinMax(pDX, age, 0, m_maxMaleAge);
```

> [!NOTE]
> 위와 같이 이러한 코드는 클래스 마법사에서 편집할 수 없으며 특수 한 서식 주석 외부 에서만 사용 해야 합니다.

## <a name="classwizard-support"></a>클래스 마법사 지원

클래스 마법사는 사용자 고유의 DDX_ 및 DDV_ 루틴을 클래스 마법사 사용자 인터페이스에 통합할 수 있도록 하 여 DDX/DDV 사용자 지정의 하위 집합을 지원 합니다. 프로젝트 또는 여러 프로젝트에서 특정 DDX 및 DDV 루틴을 다시 사용 하려는 경우에만이 작업을 수행 하면 됩니다.

이렇게 하려면 특수 항목이 DDX (이전 버전의 Visual C++ APSTUDIO.INI에이 정보를 저장 함) 또는 프로젝트의에 생성 됩니다. CLW 파일. 프로젝트의 [일반 정보] 섹션에서 특수 항목을 입력할 수 있습니다. CLW 파일 또는 Files\Microsoft Visual Studio\Visual c + + \bin 디렉터리의 DDX. CLW 파일의 [ExtraDDX] 섹션에 있습니다. 이미 존재 하지 않는 경우에는 DDX. CLW 파일이 생성 되어야 할 수 있습니다. 특정 프로젝트 에서만 사용자 지정 DDX_/DDV_ 루틴을 사용 하려면 프로젝트의 [일반 정보] 섹션에 항목을 추가 합니다. 대신 CLW 파일이 있습니다. 여러 프로젝트에서 루틴을 사용 하려면 항목을 DDX. CLW의 [ExtraDDX] 섹션에 추가 합니다.

이러한 특수 항목의 일반적인 형식은 다음과 같습니다.

> ExtraDDXCount =*n*

여기서 *n* 은 ExtraDDX의 수입니다. 다음 줄의 폼

> ExtraDDX? =*키*; *vb-키* *프롬프트*; *유형*; *Initvalue*; *DDX_Proc* [; *DDV_Proc*; *prompt1*; *arg1* [; *prompt2*; *fmt2*]]

위치? 목록에서 정의 되는 DDX 형식을 나타내는 1- *n* 입니다.

각 필드는 '; ' 문자로 구분 됩니다. 필드 및 해당 용도는 아래에 설명 되어 있습니다.

- *키*

  이 변수 형식을 사용할 수 있는 대화 상자 컨트롤을 나타내는 단일 문자 목록입니다.

  |문자|허용 된 컨트롤|
  |-|-|
  E | 편집
  C | 두 가지 상태 확인란
  c | 세 가지 상태 확인란
  R | 그룹의 첫 번째 라디오 단추
  L | 정렬 되지 않은 목록 상자
  l | 정렬 된 목록 상자
  M | 콤보 상자 (편집 항목 포함)
  N | 정렬 되지 않은 드롭 목록
  n | 정렬 된 드롭 목록
  1 | DDX 삽입을 목록의 맨 위에 추가 해야 하는 경우 (기본값은 tail에 추가) 일반적으로 ' Control ' 속성을 전송 하는 DDX 루틴에 사용 됩니다.

- *vb-키*

  이 필드는 VBX 컨트롤용 16 비트 제품 에서만 사용 됩니다. VBX 컨트롤은 32 비트 제품에서 지원 되지 않습니다.

- *prompt*

  속성 콤보 상자에 삽입할 문자열 (따옴표 제외)

- *type*

  헤더 파일에서 내보낼 형식의 단일 식별자입니다. 위의 예제에서는 DDX_Time를 사용 하 여이를 CTime으로 설정 합니다.

- *vb-키*

  이 버전에는 사용 되지 않으며 항상 비어 있어야 합니다.

- *initValue*

  초기 값이 0 이거나 비어 있습니다. 비어 있는 경우에는 구현 파일의//{{AFX_DATA_INIT 섹션에서 초기화 줄이 작성 되지 않습니다. `CString` `CTime` 올바른 초기화를 보장 하는 생성자가 있는, 등의 c + + 개체에는 빈 항목을 사용 해야 합니다.

- *DDX_Proc*

  DDX_ 프로시저의 단일 식별자입니다. C + + 함수 이름은 "DDX_"로 시작 해야 하지만 식별자에 "DDX_"를 포함 하지 않습니다 \<DDX_Proc> . 위의 예제에서 \<DDX_Proc> 식별자는 시간입니다. 클래스 마법사가 {{AFX_DATA_MAP 섹션의 구현 파일에 함수 호출을 쓰면이 이름을 DDX_에 추가 하 여 DDX_Time에 도착 합니다.

- *comment*

  이 DDX를 사용 하 여 변수에 대 한 대화 상자에 표시할 주석입니다. 여기에서 원하는 모든 텍스트를 입력 하 고 일반적으로 DDX/DDV 쌍에서 수행 하는 작업을 설명 하는 항목을 제공 합니다.

- *DDV_Proc*

  항목의 DDV 부분은 선택 사항입니다. 모든 DDX 루틴에 해당 하는 DDV 루틴이 있는 것은 아닙니다. 종종 유효성 검사 단계를 전송의 필수적인 부분으로 포함 하는 것이 더 편리할 수 있습니다. 이는 DDV 루틴이 매개 변수 없이 DDV 루틴을 지원 하지 않기 때문에 일반적으로 매개 변수가 필요 하지 않은 경우에 해당 합니다.

- *인수가*

  DDV_ 프로시저의 단일 식별자입니다. C + + 함수 이름은 "DDV_"로 시작 해야 하지만 식별자에 "DDX_"를 포함 하지 않습니다 \<DDX_Proc> .

  *인수* 뒤에는 1 또는 2 DDV args가와 야 합니다.

  - *promptN*

      편집 항목 위에 놓을 문자열입니다 (액셀러레이터에 대 한 & 사용).

  - *fmtN*

      인수 형식에 대 한 형식 문자 이며 다음 중 하나입니다.

      |문자|형식|
      |-|-|
      |일 | int|
      |u | 부호 없는 정수|
      |D | long int (즉, long)|
      |U | long unsigned (즉, DWORD)|
      |f | float|
      |F | double|
      |초 | 문자열|

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
