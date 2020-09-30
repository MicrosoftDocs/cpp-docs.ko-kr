---
title: 바이너리 편집기 (c + +)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.binary.F1
- vc.editors.binary
helpviewer_keywords:
- editors, Binary
- resources [C++], editing
- resource editors [C++], Binary editor
- Binary editor
- binary data, editing
- resources [C++], opening for binary editing
- binary data
- hexadecimal bytes in binary data
- strings [C++], searching for
- file searches [C++]
- binary data, finding
- ASCII characters, finding in binary data
- custom resources [C++]
- data resources [C++]
- resources [C++], creating
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
ms.openlocfilehash: 078d702232cde49a4666551a8d9fcbb320173450
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503531"
---
# <a name="binary-editor-c"></a>바이너리 편집기 (c + +)

> [!CAUTION]
> **바이너리 편집기** 에서 대화 상자, 이미지 또는 메뉴와 같은 리소스를 편집 하는 것은 위험 합니다. 잘못된 편집으로 리소스가 손상되어 해당 네이티브 편집기에서 읽지 못하게 될 수 있습니다.

**이진 편집기** 를 사용 하면 16 진수 또는 ASCII 형식의 이진 수준에서 리소스를 편집할 수 있습니다. 또한 [찾기 명령](/visualstudio/ide/reference/find-command) 을 사용하여 ASCII 문자열 또는 16진수 바이트를 검색할 수도 있습니다. Visual Studio 환경에서 지원 하지 않는 사용자 지정 리소스 또는 리소스 형식을 보거나 사소한 변경 작업을 수행 해야 하는 경우에만 **이진 편집기** 를 사용 합니다. Express 버전에서는 **바이너리 편집기** 를 사용할 수 없습니다.

- 새 파일에서 **이진 편집기** 를 열려면 메뉴 **파일**새 파일로 이동 하 여  >  **New**  >  **File**편집 하려는 파일 유형을 선택한 다음 **열기** 단추 옆의 드롭다운 화살표를 선택 하 고 이진 편집기 **로 열기**를 선택  >  **Binary Editor**합니다.

- 기존 파일에서 **이진 편집기** 를 열려면 메뉴 **파일**열기로 이동 하 여  >  **Open**  >  **File**편집 하려는 파일을 선택한 다음 **열기** 단추 옆의 드롭다운 화살표를 선택 하 고 이진 편집기 **로 열기**를 선택  >  **Binary Editor**합니다.

   ![바이너리 편집기](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")<br/>
   **바이너리 편집기** 에 표시 되는 대화 상자의 이진 데이터

**이진 편집기** (0X20 ~ 0x7e)에는 특정 ASCII 값만 표시 됩니다. 확장 문자는 **이진 편집기**의 오른쪽 패널 ASCII 값 섹션에 마침표로 표시 됩니다. 인쇄 가능한 문자는 ASCII 값 32 ~ 126입니다.

> [!TIP]
> **이진 편집기**를 사용 하는 동안 대부분의 경우 마우스 오른쪽 단추를 클릭 하 여 리소스 관련 명령의 바로 가기 메뉴를 표시할 수 있습니다. 사용할 수 있는 명령은 커서가 가리키는 내용에 따라 달라집니다. 예를 들어 16 진수 값을 선택 하 고 **이진 편집기** 를 가리키는 동안 마우스 오른쪽 단추를 클릭 하면 바로 가기 메뉴에 **잘라내기**, **복사**및 **붙여넣기** 명령이 표시 됩니다.

## <a name="how-to"></a>방법

**바이너리 편집기** 를 사용 하면 다음을 수행할 수 있습니다.

### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>이진 편집을 위해 Windows 데스크톱 리소스를 열려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 편집할 특정 리소스 파일을 선택합니다.

1. 리소스를 마우스 오른쪽 단추로 클릭 하 고 **이진 데이터 열기**를 선택 합니다.

> [!NOTE]
> **리소스 뷰** 창을 사용 하 여 RCDATA 또는 사용자 지정 리소스와 같이 Visual Studio에서 인식 하지 않는 형식의 리소스를 열면 **이진 편집기**에서 리소스가 자동으로 열립니다.

### <a name="to-open-a-managed-resource-for-binary-editing"></a>이진 편집을 위해 관리되는 리소스를 열려면

1. **솔루션 탐색기**에서 편집 하려는 특정 리소스 파일을 선택 합니다.

1. 리소스를 마우스 오른쪽 단추로 클릭 하 고 **연결 프로그램**을 선택 합니다.

1. **연결 프로그램** 대화 상자에서 **바이너리 편집기**를 선택합니다.

> [!NOTE]
> 관리 되는 프로젝트에서 리소스 파일로 작업 하려면 [이미지 편집기](image-editor-for-icons.md) 및 **바이너리 편집기** 를 사용할 수 있습니다. 편집할 관리되는 리소스는 연결된 리소스여야 합니다. Visual Studio 리소스 편집기에서는 포함된 리소스를 편집할 수 없습니다.

### <a name="to-edit-a-resource"></a>리소스를 편집하려면

이미 다른 편집기 창에서 편집 중인 리소스에서 **바이너리 편집기** 를 사용 하려면 먼저 다른 편집기 창을 닫습니다.

1. 편집 하려는 바이트를 선택 합니다.

   **Tab** 키는 **이진 편집기**의 16 진수 및 ASCII 섹션 사이에서 포커스를 이동 합니다. **Page Up** 및 **page Down** 키를 사용 하 여 한 번에 한 화면씩 리소스를 이동할 수 있습니다.

1. 새 값을 입력합니다.

   이 값은 16 진수 및 ASCII 섹션 모두에서 즉시 변경 되며 줄의 다음 값으로 포커스가 이동 합니다.

> [!NOTE]
> 편집기를 닫으면 **이진 편집기** 에서 변경 내용을 자동으로 적용 합니다.

### <a name="to-find-binary-data"></a>이진 데이터를 찾으려면

ASCII 문자열 또는 16 진수 바이트를 검색할 수 있습니다. 예를 들어 *hello*를 찾으려면 문자열 *hello* 또는 해당 16 진수 값 *48 65 6c 6c 6F*를 검색할 수 있습니다.

1. 메뉴로 이동 하 여 찾기를 **편집**  >  [Find](/visualstudio/ide/reference/find-command)합니다.

1. **찾을 내용** 상자의 드롭다운 목록에서 이전 검색 문자열을 선택 하거나 찾으려는 데이터를 입력 합니다.

1. **찾기** 옵션을 선택 하 고 **다음 찾기**를 선택 합니다.

### <a name="to-create-a-new-custom-or-data-resource"></a>새 사용자 지정 또는 데이터 리소스를 만들려면

일반 리소스 스크립트 (.rc) 파일 구문을 사용 하 여 별도의 파일에 리소스를 배치한 다음 **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **리소스 포함**을 선택 하 여 해당 파일을 포함 하 여 새 사용자 지정 또는 데이터 리소스를 만들 수 있습니다.

1. 사용자 지정 또는 데이터 리소스가 포함된[.rc 파일을 만듭니다](how-to-create-a-resource-script-file.md) .

   null로 끝나는 따옴표가 붙은 문자열이나 10진수, 16진수 또는 8진수 형식의 정수로 .rc 파일의 사용자 지정 데이터를 입력할 수 있습니다.

1. **솔루션 탐색기**에서 프로젝트의 .rc 파일을 마우스 오른쪽 단추로 클릭 하 고 **리소스 포함**을 선택 합니다.

1. **컴파일 타임 지시문** 상자에 `#include` 사용자 지정 리소스를 포함 하는 파일의 이름을 제공 하는 문을 입력 합니다. 예를 들면 다음과 같습니다.

    ```cpp
    #include mydata.rc
    ```

   입력한 구문 및 맞춤법이 정확한지 확인합니다. **컴파일 시간 지시문** 상자의 내용은 입력 한 대로 정확 하 게 리소스 스크립트 파일에 삽입 됩니다.

1. **확인** 을 선택 하 여 변경 내용을 기록 합니다.

사용자 지정 리소스를 만드는 또 다른 방법은 사용자 지정 리소스와 같이 외부 파일을 가져오는 것입니다. [방법: 리소스 관리](./how-to-copy-resources.md)를 참조 하세요.

> [!NOTE]
> 새 사용자 지정 또는 데이터 리소스를 만들려면 Win32가 필요 합니다.

## <a name="requirements"></a>요구 사항

없음

## <a name="see-also"></a>참고 항목

[리소스 편집기](resource-editors.md)
