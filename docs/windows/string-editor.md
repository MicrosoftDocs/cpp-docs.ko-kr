---
description: '자세한 정보: 문자열 편집기 (c + +)'
title: 문자열 편집기 (c + +)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.string.F1
- vc.editors.string
helpviewer_keywords:
- String editor
- string tables
- string tables [C++], String editor
- string editing
- string editing, string tables
- resource editors [C++], String editor
- strings [C++], editing
- strings [C++], searching
- strings [C++]
- strings [C++], adding to string tables
- string tables [C++], deleting strings
- strings [C++], deleting in string tables
- string tables [C++], adding strings
- strings [C++], moving between files
- resource script files [C++], moving strings
- string editing, moving strings between resources
- String editor [C++], moving strings between files
- resource identifiers, string properties
- string tables [C++], changing strings
- strings [C++], properties
- String editor [C++], changing properties of multiple strings
- string tables [C++], changing caption of multiple strings
- special characters, adding to strings
- ASCII characters, adding to strings
- strings [C++], formatting
- strings [C++], special characters
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
ms.openlocfilehash: 44f8d5b92b9eba805fda7607ce15230fc81748f9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263285"
---
# <a name="string-editor-c"></a>문자열 편집기 (c + +)

문자열 테이블은 애플리케이션의 모든 문자열에 대한 ID, 값 및 캡션 목록이 포함된 Windows 리소스입니다. 예를 들어 상태 표시줄 프롬프트는 문자열 테이블에 있습니다.

애플리케이션을 개발하는 동안 각 언어 또는 조건에 하나씩 여러 문자열 테이블을 만들 수 있습니다. 그러나 실행 가능 모듈에는 문자열 테이블이 하나만 포함됩니다. 테이블을 서로 다른 DLL에 삽입하면 실행 중인 애플리케이션이 여러 문자열 테이블을 참조할 수 있습니다.

문자열 테이블을 사용하면 애플리케이션을 여러 언어로 쉽게 지역화할 수 있습니다. 모든 문자열이 한 문자열 테이블에 있으면 소스 코드를 변경하지 않고 문자열과 기타 리소스를 번역하여 애플리케이션을 지역화할 수 있습니다. 이 상황은 소스 파일에서 다양 한 문자열을 수동으로 찾고 바꾸는 것 보다 더 바람직합니다.

> [!NOTE]
> Windows에서는 빈 문자열 테이블을 만들 수 없습니다. 항목 없이 문자열 테이블을 만들면 리소스 파일을 저장할 때 해당 테이블이 자동으로 삭제됩니다.

## <a name="how-to"></a>방법

**문자열 편집기** 를 사용 하면 다음을 수행할 수 있습니다.

### <a name="to-find-a-string-resource-in-the-string-table"></a>문자열 테이블에서 문자열 리소스를 찾으려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 해당 아이콘을 두 번 클릭 하 여 문자열 테이블을 엽니다.

1. 메뉴로 이동 하 여  >  **찾기 및 바꾸기** 를 편집 하 고 **찾기** 를 선택 합니다.

1. **찾을 내용** 상자의 드롭다운 목록에서 이전 검색 문자열을 선택 하거나 찾으려는 문자열의 캡션 텍스트 또는 리소스 식별자를 입력 합니다.

1. **찾기** 옵션을 선택 하 고 **다음 찾기** 를 선택 합니다.

> [!TIP]
> 파일을 검색할 때 [정규식](/visualstudio/ide/using-regular-expressions-in-visual-studio) 을 사용 하려면 **편집** 메뉴에서 **파일에서 찾기** 명령을 사용 합니다.
>
> 패턴과 일치 하는 정규식을 입력 하거나 **찾을 내용** 상자 오른쪽에 있는 단추를 선택 하 여 일반 검색 식의 목록을 표시 합니다. 이 목록에서 식을 선택 하면 **찾을 내용** 상자에 검색 텍스트로 대체 됩니다.
>
> 정규식을 사용 하는 경우 **use: Regular expressions** 확인란을 선택 해야 합니다.

### <a name="to-add-or-delete-a-string-resource"></a>문자열 리소스를 추가 또는 삭제 하려면

**문자열 편집기** 를 사용 하 여 문자열 테이블에 항목을 빠르게 삽입 하거나 삭제할 수 있습니다. 새 문자열은 테이블의 끝에 배치 되 고 다음으로 사용할 수 있는 식별자를 제공 합니다. 필요에 따라 [속성 창](/visualstudio/ide/reference/properties-window) 에서 **ID**, **값** 또는 **캡션** 속성을 편집할 수 있습니다.

**문자열 편집기** 는 이미 사용 중인 ID를 사용 하지 않도록 합니다. 이미 사용 중인 ID를 선택 하는 경우 **문자열 편집기** 에서 사용자에 게 알리고 예를 들어 일반 고유 ID를 할당 합니다 `IDS_STRING58113` .

#### <a name="to-add-a-string-table-entry"></a>문자열 테이블 항목을 추가 하려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 해당 아이콘을 두 번 클릭 하 여 문자열 테이블을 엽니다.

1. 문자열 테이블 내에서 마우스 오른쪽 단추를 클릭 하 고 **새 문자열** 을 선택 합니다.

1. **문자열 편집기** 의 **id** 드롭다운 **목록에서 Id를 선택** 하거나 직접 *id* 를 입력 합니다.

1. 필요한 경우 **값** 을 편집 합니다.

1. **캡션의** 항목을 입력 합니다.

   > [!NOTE]
   > Windows 문자열 테이블에는 Null 문자열을 사용할 수 없습니다. 문자열 테이블에 null 문자열인 항목을 만드는 경우 **이 테이블 항목에 대 한 문자열을 입력** 하 라는 메시지가 표시 됩니다.

#### <a name="to-delete-a-string-table-entry"></a>문자열 테이블 항목을 삭제 하려면

삭제할 항목을 선택 하 고 다음 중 하나를 수행 합니다.

- 메뉴 **편집**  >  **삭제** 로 이동 합니다.

- 삭제할 문자열을 마우스 오른쪽 단추로 클릭 하 고 **삭제** 를 선택 합니다.

- **Delete** 키를 누릅니다.

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>리소스 스크립트 파일 간에 문자열을 이동 하려면

1. [두 .rc 파일에서 문자열 테이블을 엽니다](../windows/how-to-create-a-resource-script-file.md).

1. 이동할 문자열을 마우스 오른쪽 단추로 클릭 하 고 **잘라내기** 를 선택 합니다.

1. 대상 **문자열 편집기** 창에 커서를 놓습니다.

1. 문자열을 이동 하려는 *.rc* 파일에서 마우스 오른쪽 단추를 클릭 하 고 **붙여넣기** 를 선택 합니다.

> [!NOTE]
> 이동 된 문자열의 **id** 또는 **값** 이 대상 파일의 기존 **id** 또는 **값** 과 충돌 하는 경우 해당 **id** 또는 이동 된 문자열의 **값** 이 변경 됩니다.

### <a name="to-change-the-properties-of-a-string-resource"></a>문자열 리소스의 속성을 변경 하려면

내부 편집을 사용 하 여 **ID**, **값** 및 **캡션** 속성을 변경할 수 있습니다.

> [!NOTE]
> [속성 창](/visualstudio/ide/reference/properties-window)에서 문자열의 속성을 편집할 수도 있습니다.

#### <a name="to-change-a-string-or-its-identifier"></a>문자열이 나 해당 식별자를 변경 하려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 해당 아이콘을 두 번 클릭 하 여 문자열 테이블을 엽니다.

1. 편집할 문자열을 선택 하 고 **ID**, **값** 또는 **캡션** 열을 두 번 클릭 한 후 다음을 수행할 수 있습니다.

   - **Id 드롭다운 목록** 에서 **id** 를 선택 하거나 직접 *id* 를 입력 합니다.

   - **값** 열에 다른 숫자를 입력 합니다.

   - **Caption** 열에서 편집을 입력 합니다.

#### <a name="to-change-the-caption-property-of-multiple-string-resources"></a>여러 문자열 리소스의 caption 속성을 변경 하려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 해당 아이콘을 두 번 클릭 하 여 문자열 테이블을 엽니다.

1. **Ctrl** 키를 누른 채 각 항목을 선택 하 여 변경할 문자열을 선택 합니다.

1. [속성 창](/visualstudio/ide/reference/properties-window)에서 변경 하려는 속성의 새 값을 입력 합니다.

1. **Enter** 키를 누릅니다.

### <a name="to-add-formatting-or-special-characters-to-a-string-resource"></a>문자열 리소스에 형식 지정 또는 특수 문자를 추가 하려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 해당 아이콘을 두 번 클릭 하 여 문자열 테이블을 엽니다.

1. 수정 하려는 문자열을 선택 합니다.

1. [속성 창](/visualstudio/ide/reference/properties-window)에서 아래에 나열 된 표준 이스케이프 시퀀스를 **캡션** 상자의 텍스트에 추가 하 고 **enter** 키를 누릅니다.

   |이를 가져오려면|입력 ...|
   |-----------------|---------------|
   | 줄 바꿈 | \\n |
   | 캐리지 리턴 | \\& |
   | 탭 | \\t |
   | 백슬래시(\\) | \\\\ |
   | ASCII 문자 | \\ddd (8 진수 표기법) |
   | 경고 (벨) | \\a |

   > [!NOTE]
   > **문자열 편집기** 는 이스케이프 된 ASCI 문자의 전체 집합을 지원 하지 않습니다. 위에 나열 된 항목만 사용할 수 있습니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[리소스 편집기](../windows/resource-editors.md) 
 [문자열](/windows/win32/menurc/strings)<br/>
[문자열 정보](/windows/win32/menurc/about-strings)<br/>
[창 레이아웃 사용자 지정](/visualstudio/ide/customizing-window-layouts-in-visual-studio)
