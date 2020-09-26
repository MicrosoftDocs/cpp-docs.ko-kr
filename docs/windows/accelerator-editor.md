---
title: 액셀러레이터 키 편집기 (c + +)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.accelerator.F1
- vc.editors.accelerator
helpviewer_keywords:
- accelerator tables [C++], editing
- tables [C++], accelerator key
- accelerator keys [C++]
- resource editors [C++], Accelerator editor
- keyboard shortcuts [C++], Accelerator editor
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
- VIRTKEY
- Key property
- ID property
- accelerator tables [C++], editing
- keyboard shortcuts [C++], editing in an accelerator table
- searching, in accelarator tables
- accelerator tables [C++], finding entries
- accelerator tables [C++], adding entries
- New Accelerator command
- accelerator tables [C++], deleting entries
- keyboard shortcuts [C++], deleting entry from accelerator table
- accelerator tables [C++], copying entries
- rc files [C++], moving an accelerator table entry
- .rc files [C++], moving accelerator table entries
- accelerator tables [C++], moving entries
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: 013c30b6-5d61-4f1c-acef-8bd15bed7060
ms.openlocfilehash: c98ff1fd44b73b3f204e9b952836c387f7f21146
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353092"
---
# <a name="accelerator-editor-c"></a>액셀러레이터 키 편집기 (c + +)

액셀러레이터 키 테이블은 바로 가기 키와 연결 된 명령 식별자의 목록을 포함 하는 c + + Windows 리소스입니다. 프로그램에는 액셀러레이터 키 테이블이 두 개 이상 있을 수 있습니다.

일반적으로 액셀러레이터 키는 메뉴 또는 도구 모음에서도 사용할 수 있는 프로그램 명령에 대한 바로 가기 키로 사용됩니다. 그러나 연결된 사용자 인터페이스 개체가 없는 명령에 대한 키 조합을 정의하는 데 액셀러레이터 키 테이블을 사용할 수 있습니다.

> [!TIP]
> **액셀러레이터 키 편집기**를 사용 하는 경우 마우스 오른쪽 단추를 클릭 하 여 자주 사용 되는 명령의 바로 가기 메뉴를 표시 합니다. 사용할 수 있는 명령은 포인터가 가리키는 내용에 따라 달라집니다.

[클래스 뷰](/visualstudio/ide/viewing-the-structure-of-code) 를 사용하여 액셀러레이터 키 명령을 코드에 연결할 수 있습니다. 미리 정의 된 액셀러레이터 키 목록은 [액셀러레이터 키](predefined-accelerator-keys.md)를 참조 하세요.

> [!NOTE]
> Windows에서는 빈 액셀러레이터 키 테이블을 만들 수 없습니다. 항목이 없는 액셀러레이터 키 테이블을 만들 경우 해당 테이블을 저장할 때 테이블이 자동으로 삭제됩니다.

## <a name="accelerator-properties"></a>액셀러레이터 키 속성

언제 든 지 [속성 창](/visualstudio/ide/reference/properties-window) 액셀러레이터 키 속성을 설정할 수 있습니다. 액셀러레이터 키 **편집기** 를 사용 하 여 액셀러레이터 키 테이블의 액셀러레이터 속성을 수정할 수도 있습니다. **속성** 창이 나 **액셀러레이터 키 편집기** 를 사용 하 여 변경한 내용이 동일한 결과를가지고, 편집 내용이 액셀러레이터 키 테이블에 즉시 반영 됩니다.

**ID** 속성은 프로그램 코드의 각 액셀러레이터 키 테이블 항목을 참조 합니다. 이 항목은 사용자가 액셀러레이터 키 또는 키 조합을 누를 때 프로그램이 수신 하는 명령 값입니다. 액셀러레이터 키를 메뉴 항목과 동일 하 게 만들려면 액셀러레이터 키 테이블의 **id** 가 메뉴 리소스의 **id** 와 동일한 경우에만 **id** 를 동일 하 게 만듭니다.

각 액셀러레이터 **ID** 에는 **한정자**, **키**및 **형식** 의 세 가지 속성이 있습니다.

**한정자** 속성은 액셀러레이터 키에 대 한 제어 키 조합을 설정 합니다.

> [!NOTE]
> **속성** 창에서 **Modifier** 속성은 각각 독립적으로 제어 될 수 있는 세 개의 개별 **부울** 속성으로 표시 됩니다. **Alt**, **Ctrl**, **Shift**.

다음은 액셀러레이터 키 테이블의 **Modifier** 속성에 대 한 올바른 항목입니다.

   |값|Description|
   |-----------|-----------------|
   |**없음**|사용자는 **키** 값만 누릅니다.<br/><br/>이 값은 일반적으로 ^ A부터 ^ Z (**ctrl + a** 부터 **ctrl + z**까지)로 해석 되는 026을 통해 ASCII/ANSI 값 001에서 사용 됩니다.|
   |**#B0**|사용자는 **키** 값 앞에 **Alt** 키를 눌러야 합니다.|
   |**T**|사용자는 **키** 값 앞에 **ctrl** 키를 눌러야 하며 ASCII 형식으로는 사용할 수 없습니다.|
   |**Shift**|사용자는 **키** 값 앞에 **shift** 키를 눌러야 합니다.|
   |**Ctrl + Alt**|사용자는 **키** 값 앞에 **ctrl** 및 **ALT** 키를 눌러야 하며 ASCII 형식으로는 사용할 수 없습니다.|
   |**Ctrl + Shift**|사용자는 **키** 값 앞에 **ctrl** **+ Shift** 를 눌러야 하며 ASCII 형식으로는 사용할 수 없습니다.|
   |**Alt + Shift**|사용자는 키 값 앞에 **alt** 키를 누르고 **Shift** **키** 를 눌러야 하며 ASCII 형식으로는 사용할 수 없습니다.|
   |**Ctrl + Alt + Shift**|사용자는 **키** 값 앞에 **ctrl**, **Alt**및 **Shift** 키를 눌러야 하며 ASCII 형식으로는 사용할 수 없습니다.|

**키** 속성은 액셀러레이터 키로 사용할 실제 키를 설정 합니다.

액셀러레이터 키 테이블의 **키** 속성에 대 한 올바른 항목은 다음과 같습니다.

   |값|Description|
   |-----------|-----------------|
   |0에서 255 사이의 정수 (10 진수 형식)입니다.|값은 다음과 같이 값이 ASCII 또는 ANSI로 처리 되는지 여부를 결정 합니다.<br/><br/>   -단일 자릿수 숫자는 항상 ASCII 또는 ANSI 값이 아니라 해당 키로 해석 됩니다.<br/>   -1부터 26 까지의 값이 0 이면 ^ A부터 ^ Z로 해석 됩니다 .이 값은 **Ctrl** 키를 누르고 있을 때 누르는 영문자의 ASCII 값을 나타냅니다.<br/>   -27-32의 값은 항상 032의 3 자리 10 진수 값으로 해석 됩니다.<br/>   -값이 0 보다 앞에 있든, 0부터 255 033 까지의 값은 ANSI 값으로 해석 됩니다.|
   |단일 키보드 문자입니다.|대문자 A-z 또는 숫자 0-9은 ASCII 또는 가상 키 값 중 하나일 수 있습니다. 다른 문자는 ASCII 전용입니다.|
   |A-Z 범위의 단일 키보드 문자 (대문자 전용)는 캐럿 (^)이 앞에 옵니다 (예: ^ C).|이 옵션은 **ctrl** 키를 누른 상태에서 키를 누를 때 키의 ASCII 값을 입력 합니다.|
   |모든 유효한 가상 키 식별자입니다.|액셀러레이터 키 테이블의 드롭다운 **키** 상자에는 표준 가상 키 식별자 목록이 포함 되어 있습니다.|

> [!NOTE]
> ASCII 값을 입력할 때 **한정자** 속성 옵션이 제한 됩니다. 사용할 수 있는 유일한 제어 키는 **Alt** 키입니다.

> [!TIP]
> 액셀러레이터 키를 정의 하는 바로 가기는 액셀러레이터 키 테이블에서 항목 또는 여러 항목을 마우스 오른쪽 단추로 클릭 한 다음, **다음 키 형식화** 를 선택 하 고 키보드에서 키 또는 키 조합을 누릅니다.
>
> **편집** 메뉴에서이 **다음 키 입력** 명령을 사용할 수도 있습니다.

**Type** 속성은 액셀러레이터 **ID** 와 연결 된 바로 가기 키 조합이 ASCII/ANSI 키 값 또는 가상 키 (VIRTKEY) 조합으로 해석 되는지 여부를 결정 합니다.

- **Type** 속성이 **ASCII**인 경우 **Modifier** 속성은 또는 일 수 있습니다 `None` `Alt` . 또는 키 앞에를 사용 하 여 지정 된 대로 **Ctrl** 키를 사용 하는 액셀러레이터 키를 사용할 수 있습니다 `^` .

- **Type** 속성이 **VIRTKEY**인 경우 **한정자** 및 **키** 값의 모든 조합이 유효 합니다.

> [!NOTE]
> 액셀러레이터 키 테이블에 값을 입력 하 고 값을 ASCII/ANSI로 처리 하려면 테이블에서 항목에 대 한 **유형을** 선택 하 고 드롭다운 목록에서 **ASCII** 를 선택 합니다. 그러나 **편집** 메뉴에서 **다음 키 입력** 명령을 사용 하 여 **키**를 지정 하는 경우에는 **키** 코드를 입력 *하기 전에* **Type** 속성을 **VIRTKEY** 에서 **ASCII** 로 변경 해야 합니다.

## <a name="accelerator-tables"></a>액셀러레이터 키 테이블

C + + 프로젝트에서는 **액셀러레이터 키 편집기**의 바로 가기 편집 기능을 사용 하 여 액셀러레이터 키 테이블을 직접 편집할 수 있습니다.

다음 절차에서는 표준 속성 페이지 사용을 참조 하지만 내부 편집 및 속성 페이지 메서드의 결과가 동일 합니다. 속성 페이지를 사용 하거나 내부 편집을 사용 하 여 변경한 내용은 액셀러레이터 키 테이블에 즉시 반영 됩니다.

### <a name="to-edit-in-an-accelerator-table"></a>액셀러레이터 키 테이블에서 편집하려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 해당 아이콘을 두 번 클릭 하 여 액셀러레이터 키 테이블을 엽니다.

1. 테이블에서 항목을 선택 하 고 바로 편집을 활성화 하려면 선택 합니다.

1. 드롭다운 콤보 상자에서 선택 하거나 원하는 위치를 입력 하 여 변경 합니다.

   - **ID**의 경우 목록에서 선택 하거나 입력 하 여 편집 합니다.

   - **한정자**의 경우 목록에서을 선택 합니다.

   - **키**의 경우 목록에서 선택 하거나 입력 하 여 편집 합니다.

   - **유형**의 경우 목록에서 **ASCII** 또는 **VIRTKEY** 를 선택 합니다.

### <a name="to-find-an-entry-in-an-open-accelerator-table"></a>열린 액셀러레이터 키 테이블에서 항목을 찾으려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 해당 아이콘을 두 번 클릭 하 여 액셀러레이터 키 테이블을 엽니다.

1. 열의 내용을 사전순으로 정렬 하려면 열 머리글을 선택 합니다. 예를 들어 **id** 를 선택 하 여 액셀러레이터 키 테이블의 모든 id를 사전순으로 표시 합니다.

   그런 다음 목록을 검색하고 항목을 찾을 수 있습니다.

### <a name="to-add-an-entry-to-an-accelerator-table"></a>액셀러레이터 키 테이블에 항목을 추가하려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 해당 아이콘을 두 번 클릭 하 여 액셀러레이터 키 테이블을 엽니다.

1. 액셀러레이터 키 테이블 내에서 마우스 오른쪽 단추를 클릭 하 고 **새 액셀러레이터 키**를 선택 하거나 테이블 맨 아래에 있는 빈 행 항목을 선택 합니다.

1. **Id 상자의 드롭다운** 목록에서 **id** 를 선택 하거나 **id** 상자에 새 *id* 를 입력 합니다.

1. 액셀러레이터 키로 사용 하려는 *키* 를 입력 하거나 마우스 오른쪽 단추를 클릭 하 고 **입력 한 다음** 키를 선택 하 여 키 조합을 설정 하거나 메뉴에서 형식화 된 다음 키 **편집**으로 이동  >  **Next Key Typed**합니다.

1. **한정자** 와 **형식**(필요한 경우)을 변경 하 고 **enter**키를 누릅니다.

> [!NOTE]
> 정의한 모든 액셀러레이터 키가 고유한지 확인합니다. 동일한 ID에 할당 된 여러 키 조합을 사용할 수 있습니다. 예를 들어 **Ctrl** + **P** 와 **F8** 모두 ID_PRINT에 할당 될 수 있습니다. 그러나 두 개 이상의 ID에 할당 된 키 조합을 사용 하는 경우, 예를 들어 **Ctrl** + ID_SPELL_CHECK 및 ID_THESAURUS 둘 다에 할당 된 Ctrl**Z** 가 제대로 작동 하지 않습니다.

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>액셀러레이터 키 테이블에서 항목을 삭제하려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 해당 아이콘을 두 번 클릭 하 여 액셀러레이터 키 테이블을 엽니다.

1. 삭제할 항목을 선택 하거나 **Ctrl** 또는 **Shift** 키를 누른 채 여러 항목을 선택 하려면 선택 합니다.

1. 마우스 오른쪽 단추를 클릭 하 고 **삭제**를 선택 하거나 메뉴에서 삭제 **편집**으로 이동  >  **Delete**합니다.

> [!TIP]
> **Delete 키를** 눌러 삭제를 삭제할 수도 있습니다.

### <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>액셀러레이터 키 테이블 항목을 다른 리소스 스크립트 파일로 이동/복사

1. 두 리소스 스크립트 파일 모두에서 액셀러레이터 키 테이블을 열고 이동 하려는 항목을 선택 합니다.

1. **편집** 메뉴에서 **복사** 또는 **잘라내기**를 선택 합니다.

1. 대상 리소스 스크립트 파일에서 항목을 선택 하 고 **편집** 메뉴에서 **붙여넣기**를 선택 합니다.

> [!NOTE]
> 복사 및 붙여넣기의 바로 가기 키를 사용할 수도 있습니다.

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>여러 액셀러레이터 키의 속성을 변경 하려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 해당 아이콘을 두 번 클릭 하 여 액셀러레이터 키 테이블을 엽니다.

1. **Ctrl** 키를 누른 채 각 항목을 선택 하 여 변경할 액셀러레이터 키를 선택 합니다.

1. [속성 창](/visualstudio/ide/reference/properties-window) 로 이동 하 고 선택한 모든 액셀러레이터 키를 공유 하려는 값을 입력 합니다.

> [!NOTE]
> 각 한정자 값은 **속성** 창에 부울 속성으로 표시 됩니다. **속성** 창에서 한정자 값을 변경 하는 경우 액셀러레이터 키 테이블은 이전에 있던 한정자를 추가 하는 것으로 새 한정자를 처리 합니다. 따라서 한정자 값을 설정 하는 경우 모든 액셀러레이터 키가 동일한 **한정자** 설정을 공유 하도록 모든 한정자를 설정 해야 합니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[리소스 편집기](resource-editors.md)<br/>
[액셀러레이터 키](predefined-accelerator-keys.md)<br/>
