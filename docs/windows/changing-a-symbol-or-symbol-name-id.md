---
title: '방법: 기호 관리'
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.changing
- vc.editors.symbol.restrictions.name
- vc.editors.symbol.changing.value
- vc.editors.symbol.restrictions.value
- vc.editors.symbol.changing.header
- vc.editors.symbol.changing.unassigned
- vc.editors.symbol.shared.calculated
helpviewer_keywords:
- symbol names
- symbols [C++], names
- restrictions, symbol names
- numeric values
- symbols [C++], numeric values
- numeric values, changing symbols
- symbols [C++], value restrictions
- restrictions, symbol values
- resource files [C++], multiple
- Resource Includes dialog box [C++]
- symbol header files [C++], changing names
- symbols [C++], symbol header files
- Resource.h
- symbols [C++], unassigned
- Change Symbol dialog box [C++]
- unassigned symbols
- symbols [C++], deleting
- symbols [C++], read-only
- symbols [C++], shared
- symbols [C++], calculated
- read-only symbols
- symbol directives
- calculated symbols
- shared symbols
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
ms.openlocfilehash: 67a5c801c13038e7215473edecc2d41a8f7086e0
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505722"
---
# <a name="how-to-manage-symbols"></a>방법: 기호 관리

새 리소스 또는 리소스 개체를 만들 때 개발 환경에서는 기본 기호 이름 (예:)을 할당 `IDD_DIALOG1` 합니다. [속성 창](/visualstudio/ide/reference/properties-window) 를 사용 하 여 기본 기호 이름을 변경 하거나 이미 리소스와 연결 된 기호의 이름을 변경할 수 있습니다.

단일 리소스와 연결 된 기호의 경우 **속성** 창을 사용 하 여 기호 값을 변경할 수도 있습니다. [리소스 기호 대화 상자](./creating-new-symbols.md) 를 사용 하 여 현재 리소스에 할당 되지 않은 기호의 값을 변경할 수 있습니다.

일반적으로 모든 기호 정의는에 저장 됩니다 `Resource.h` . 그러나 예를 들어 같은 디렉터리에서 둘 이상의 리소스 파일을 사용할 수 있도록 이 포함 파일 이름을 변경해야 할 수 있습니다.

> [!NOTE]
> 프로젝트에 .rc 파일이 아직 없는 경우 [방법: 리소스 만들기](how-to-create-a-resource-script-file.md)를 참조 하세요.

## <a name="symbol-name-restrictions"></a>기호 이름 제한

기호 이름에 대한 제한은 다음과 같습니다.

- 헤더 파일에서 기호 정의 충돌을 방지 하려면 모든 [기호가](symbols-resource-identifiers.md) 응용 프로그램 범위 내에서 고유 해야 합니다.

- 기호 이름에 유효한 문자는 A-Z, a-z, 0-9 및 밑줄(_)입니다.

- 기호 이름은 숫자로 시작할 수 없으며 247 자로 제한 됩니다.

- 기호 이름에는 공백을 사용할 수 없습니다.

- 기호 이름에 대/소문자를 구분 하지 않지만 첫 번째 기호 정의의 대/소문자는 유지 됩니다.

   기호를 정의하는 헤더 파일은 리소스 컴파일러/편집기 및 C++ 프로그램에서 리소스 파일에 정의된 리소스를 참조하는 데 사용됩니다. 대/소문자만 다른 두 기호 이름에 대해 C++ 프로그램은 별도의 두 기호로 보지만 리소스 컴파일러/편집기는 두 이름이 하나의 단일 기호를 나타내는 것으로 봅니다.

> [!NOTE]
> 아래에 설명 된 표준 기호 이름 구성표 (ID * _ [keyword])를 따르지 않고 기호 이름이 리소스 스크립트 컴파일러에 알려진 키워드와 동일 하 게 발생 하는 경우 리소스 스크립트 파일을 작성 하려고 하면 진단 하기 어려운 무작위 오류 생성이 발생 합니다. 이를 방지하려면 표준 이름 지정 체계를 준수하세요.

기호 이름에는 해당 이름이 나타내는 리소스 또는 개체의 종류를 나타내는 설명 접두사가 있습니다. 이러한 설명 접두사는 텍스트 조합 ID로 시작합니다. MFC (Microsoft Foundation Class) 라이브러리는 다음 표에 나와 있는 기호 명명 규칙을 사용 합니다.

|범주|접두사|기능|
|--------------|------------|---------|
|리소스|IDR_, IDD_, IDC_, IDI_, IDB_|액셀러레이터 키 또는 메뉴 (및 연결 된 리소스 또는 사용자 지정 리소스), 대화 상자, 커서, 아이콘, 비트맵|
|메뉴 항목|ID_|Menu item|
|명령|ID_|명령|
|컨트롤 및 자식 창|IDC_|제어|
|문자열|IDS_|문자열 테이블의 문자열|
|MFC|AFX_|미리 정의된 MFC 기호에 예약됨|

### <a name="to-change-a-symbol-name-id"></a>기호 이름 (ID)을 변경 하려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 리소스를 선택 합니다.

1. **속성** 창에서 새 기호 이름을 입력 하거나 **ID** 상자의 기존 기호 목록에서 선택 합니다.

   새 기호 이름을 입력 하면 값이 자동으로 할당 됩니다.

> [!NOTE]
> [리소스 기호 대화 상자](./creating-new-symbols.md) 를 사용 하 여 현재 리소스에 할당 되지 않은 기호의 이름을 변경할 수 있습니다.

## <a name="symbol-value-restrictions"></a>기호 값 제한

기호 값은 전처리기 지시문에 대 한 일반적인 방법으로 표현 되는 정수일 수 있습니다 `#define` . 다음은 기호 값의 몇 가지 예입니다.

```
18
4001
0x0012
-3456
```

액셀러레이터 키, 비트맵, 커서, 대화 상자, 아이콘, 메뉴, 문자열 테이블 및 버전 정보와 같은 리소스에 대 한 기호 값은 0에서 32767 사이의 10 진수 여야 하지만 16 진수는 될 수 없습니다. 대화 상자 컨트롤이나 문자열 테이블의 개별 문자열 같이 리소스 일부에 대한 기호 값은 0에서 65,534 사이이거나 -32,768에서 32,767 사이일 수 있습니다. 숫자 범위에 대 한 자세한 내용은 [TN023: 표준 MFC 리소스](../mfc/tn023-standard-mfc-resources.md)를 참조 하세요.

리소스 기호는 16 비트 숫자입니다. 이러한 값은 signed 또는 unsigned로 입력할 수 있지만 내부적으로는 부호 없는 정수로 사용 되므로 음수는 해당 양수 값으로 캐스팅 됩니다.

기호 값의 몇 가지 제한 사항은 다음과 같습니다.

- Visual Studio 개발 환경 및 MFC에서는 일부 숫자 범위를 특별한 용도로 사용합니다. 가장 중요한 비트 세트를 사용하는 모든 숫자(부호에 따라 -32,768 ~ -1 또는 32,768 ~ 65,534)는 MFC에 의해 예약되었습니다.

- 다른 기호 문자열을 사용 하 여 기호 값을 정의할 수 없습니다. 예를 들어 다음 기호 정의는 지원 되지 않습니다.

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- 인수가 값 정의로 전처리기 매크로를 사용할 수 없습니다. 다음 예제는 컴파일 타임에이 반환 되는 결과에 관계 없이 유효한 식이 아닙니다 `ID` .

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

- 애플리케이션에 식으로 정의된 기호를 포함하는 기존 파일이 있을 수 있습니다.

### <a name="to-change-a-symbol-value"></a>기호 값을 변경 하려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 리소스를 선택 합니다.

1. **속성** 창에서 기호 이름 다음에 등호를 입력 하 고 **ID** 상자에 정수를 입력 합니다. 예를 들면 다음과 같습니다.

    ```
    IDC_EDITNAME=5100
    ```

   새 값은 다음에 프로젝트를 저장할 때 기호 헤더 파일에 저장됩니다. 기호 이름만 ID 상자에 표시 되 고 유효성 검사 후에 등호 및 값이 표시 되지 않습니다.

## <a name="change-or-delete-symbols"></a>기호 변경 또는 삭제

[리소스 기호 대화 상자](./creating-new-symbols.md)에서 리소스 또는 개체에 아직 할당 되지 않은 기존 기호를 편집 하거나 삭제할 수 있습니다.

### <a name="to-change-an-unassigned-symbol"></a>할당되지 않은 기호를 변경하려면

1. **이름** 상자에서 할당 되지 않은 기호를 선택 하 고 **변경**을 선택 합니다.

1. **기호 변경** 대화 상자에서 제공 하는 상자에서 기호의 이름 또는 값을 편집 합니다.

> [!NOTE]
> 리소스 또는 개체에 할당 된 기호를 변경 하려면 리소스 편집기 또는 **속성** 창을 사용 해야 합니다.

### <a name="to-delete-an-unassigned-unused-symbol"></a>할당되지 않은(사용되지 않은) 기호를 삭제하려면

**리소스 기호** 대화 상자에서 삭제 하려는 기호를 선택 하 고 **삭제**를 선택 합니다.

> [!NOTE]
> 리소스 파일에서 사용 되지 않은 기호를 삭제 하기 전에 해당 기호를 프로그램의 다른 위치 또는 컴파일 시간에 포함 된 리소스 파일에서 사용 하지 않는지 확인 합니다.

## <a name="include-symbols"></a>기호 포함

다른 애플리케이션에서 만든 리소스 파일을 처음으로 개발 환경에서 읽는 경우 포함된 헤더 파일을 모두 읽기 전용으로 표시합니다. 그러나 [리소스 내용 대화 상자](./how-to-include-resources-at-compile-time.md) 를 사용 하 여 읽기 전용 기호 헤더 파일을 더 추가할 수 있습니다.

읽기 전용 기호 정의를 사용하려는 한 가지 이유는 여러 프로젝트에서 공유하려고 하는 기호 파일 때문입니다.

또한 단순 정수 대신 식을 사용하여 기호 값을 정의하는 기호 정의를 사용하는 기존 리소스가 있는 경우에 포함된 기호 파일을 사용할 수 있습니다. 다음은 그 예입니다.

```cpp
#define   IDC_CONTROL1 2100
#define   IDC_CONTROL2 (IDC_CONTROL1+1)
```

다음과 같은 경우 환경에서 이러한 계산된 기호를 올바르게 해석합니다.

- 계산된 기호가 읽기 전용 기호 파일에 배치됩니다.

- 리소스 파일에 이러한 계산된 기호가 이미 할당된 리소스가 포함되어 있습니다.

- 숫자 식이 필요합니다.

> [!NOTE]
> 문자열이나 숫자 식이 필요한 경우에는 식이 계산되지 않습니다.

### <a name="to-include-shared-read-only-symbols-in-your-resource-file"></a>리소스 파일에 공유(읽기 전용) 기호를 포함하려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 *.rc* 파일을 마우스 오른쪽 단추로 클릭 하 고 [리소스 포함](./how-to-include-resources-at-compile-time.md)을 선택 합니다.

1. 읽기 전용 **기호 지시문** 상자에서 `#include` 컴파일러 지시문을 사용 하 여 읽기 전용 기호를 보관할 파일을 지정 합니다.

   파일은 `Resource.h` 기본 기호 헤더 파일에 일반적으로 사용 되는 파일 이름 이므로 호출 하지 마십시오.

   > [!NOTE]
   > **읽기 전용 기호 지시문** 상자에 입력 한 내용은 입력 한 대로 정확 하 게 리소스 파일에 포함 됩니다. 입력한 내용에 맞춤법이나 구문 오류가 없는지 확인하세요.

   읽기 전용 **기호 지시문** 상자를 사용 하 여 기호 정의만 있는 파일을 포함 합니다. 리소스 정의를 포함 하지 마세요. 파일이 저장 될 때 중복 리소스 정의가 생성 됩니다.

1. 지정한 파일에 기호를 배치합니다.

   이러한 방식으로 포함 된 파일의 기호는 리소스 파일을 열 때마다 평가 되지만 파일을 저장할 때 디스크에서 대체 되지 않습니다.

1. **확인**을 선택합니다.

### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>리소스 기호 헤더 파일의 이름을 변경하려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 *.rc* 파일을 마우스 오른쪽 단추로 클릭 하 고 [리소스 포함](./how-to-include-resources-at-compile-time.md)을 선택 합니다.

1. **기호 헤더 파일** 상자에 포함 파일의 새 이름을 입력 합니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[리소스 식별자 (기호)](symbols-resource-identifiers.md)<br/>
[방법: 기호 만들기](creating-new-symbols.md)<br/>
[미리 정의 된 기호 Id](predefined-symbol-ids.md)<br/>
