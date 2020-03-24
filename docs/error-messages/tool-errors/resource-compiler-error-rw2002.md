---
title: 리소스 컴파일러 오류 RW2002
ms.date: 11/04/2016
f1_keywords:
- RW2002
helpviewer_keywords:
- RW2002
ms.assetid: b1d1a49b-b50b-4b0b-9f09-c7762e2dbe8f
ms.openlocfilehash: 9c5c2824778a679627bd3008276849890f43ac7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190692"
---
# <a name="resource-compiler-error-rw2002"></a>리소스 컴파일러 오류 RW2002

구문 분석 오류

### <a name="to-fix-by-checking-the-following-possible-causes"></a>다음과 같은 가능한 원인을 확인하여 수정하려면

1. **액셀러레이터 키 형식이 필요 합니다 (ASCII 또는 VIRTKEY).**

   `type` ACCELERATORS **문의** 필드는 ASCII 또는 VIRTKEY 값을 포함해야 합니다.

1. **액셀러레이터 키 테이블에 BEGIN이 필요 합니다.**

   **BEGIN** 키워드가 **ACCELERATORS** 키워드 바로 뒤에 와야 합니다.

1. **대화 상자에 BEGIN이 필요 합니다.**

   **BEGIN** 키워드는 **DIALOG** 키워드 바로 뒤에와 야 합니다.

1. **메뉴에 BEGIN이 필요 합니다.**

   **BEGIN** 키워드가 **MENU** 키워드 바로 뒤에 와야 합니다.

1. **RCData에서 BEGIN이 필요 합니다.**

   **BEGIN** 키워드가 **RCDATA** 키워드 바로 뒤에 와야 합니다.

1. **문자열 테이블에 BEGIN 키워드가 필요 합니다.**

   **BEGIN** 키워드는 **stringtable** 키워드 바로 뒤에와 야 합니다.

1. **문자열 상수를 다시 사용할 수 없습니다.**

   **Stringtable** 문에서 같은 값을 두 번 사용 합니다. 겹치는 소수 및 16 진수 값을 혼합 하지 않아야 합니다. **Stringtable** 의 각 ID는 고유 해야 합니다. 효율성을 최대화 하려면 16의 배수로 시작 하는 연속 상수를 사용 합니다.

1. **제어 문자가 범위 [^ A-^ Z]를 벗어났습니다.**

   **ACCELERATORS** 문의 제어 문자가 잘못되었습니다. 캐럿( **^** ) 뒤의 문자는 A에서 Z(포함) 사이여야 합니다.

1. **빈 메뉴는 허용 되지 않습니다.**

   **Menu 문에 메뉴** 항목이 정의 되기 전에 **END** 키워드가 표시 됩니다. 리소스 컴파일러는 빈 메뉴를 허용 하지 않습니다. **메뉴** 문 내에 여는 따옴표가 없는지 확인 합니다.

1. **대화 상자에 끝이 필요 합니다.**

   **End** 키워드는 **DIALOG** 문의 끝에 있어야 합니다. 앞의 문에서 왼쪽에 열려 있는 따옴표가 없는지 확인 합니다.

1. **메뉴에 END가 필요 합니다.**

   **MENU** 문의 끝에 **END** 키워드가 와야 합니다. 열려 있는 따옴표나 일치하지 않는 **BEGIN** 및 **END** 문 쌍이 없는지 확인합니다.

1. **액셀러레이터 키 테이블에 쉼표가 필요 합니다.**

   리소스 컴파일러에서는 `event` ACCELERATORS *문의* 및 **idvalue** 필드 사이에 쉼표가 있어야 합니다.

1. **컨트롤 클래스 이름이 필요 합니다.**

   **DIALOG** 문에서 **CONTROL** 문의 `class` 필드는 BUTTON, COMBOBOX, EDIT, LISTBOX, SCROLLBAR, STATIC 또는 사용자 정의 형식 중 하나 여야 합니다. 클래스의 철자가 정확한 지 확인 합니다.

1. **글꼴 이름이 필요 합니다.**

   *DIALOG* 문의 FONT 옵션에 있는 **typeface** 필드는 큰따옴표로 묶인 ASCII 문자열이어야 합니다. 이 필드는 글꼴의 이름을 지정합니다.

1. **Menuitem에 대 한 ID 값이 필요 합니다.**

   **MENU** 문에 메뉴 리소스를 식별하는 이름이나 번호를 지정하는 *menuID* 필드가 포함되어야 합니다.

1. **메뉴 문자열이 필요 합니다.**

   각 **MENUITEM** 및 **POPUP** 문은 메뉴 항목 또는 팝업 메뉴의 이름을 지정하는 큰따옴표로 묶인 문자열인 *text* 필드를 포함해야 합니다. **MENUITEM SEPARATOR** 문에는 따옴표 붙은 문자열이 필요 하지 않습니다.

1. **숫자 명령 값이 필요 합니다.**

   리소스 컴파일러에서 **액셀러레이터 키** 에 숫자 *idvalue* 필드가 필요 합니다. `#define` 상수를 사용 하 여 값을 지정 했는지와 상수의 철자가 정확한 지 확인 합니다.

1. **문자열 테이블에 숫자 상수가 필요 합니다.**

   `#define` 문에 정의된 숫자 상수는 **STRINGTABLE** 문의 **BEGIN** 키워드 바로 뒤에 와야 합니다.

1. **숫자 포인트 크기가 필요 합니다.**

   *DIALOG* 문의 FONT 옵션에 있는 **pointsize** 필드가 정수 포인트 크기 값이어야 합니다.

1. **숫자 대화 상자 상수가 필요 합니다.**

   **DIALOG** 문에는 *x, y, width*및 *height* 필드의 정수 값이 필요 합니다. 이러한 값이 **DIALOG** 키워드 뒤에 포함 되 고 음수가 아닌지 확인 합니다.

1. **STRINGTABLE에 문자열이 필요 합니다.**

   *STRINGTABLE* 문에서 각 **stringid** 값 뒤에 문자열이 있어야 합니다.

1. **문자열 또는 상수 액셀러레이터 키 명령이 필요 합니다.**

   리소스 컴파일러에서 액셀러레이터 키에 설정되는 키 종류를 확인할 수 없습니다. `event` ACCELERATORS **문의** 필드가 잘못되었을 수 있습니다.

1. **ID에 숫자가 필요 합니다.**

   **DIALOG** 문에서 control 문의 `id` 필드에는 숫자가 필요 합니다. 컨트롤 ID에 대해 숫자나 `#define` 문이 있는지 확인 합니다.

1. **대화 상자 클래스에 따옴표 붙은 문자열이 필요 합니다.**

   `class` DIALOG **문의 CLASS 옵션에 있는** 필드는 큰따옴표로 묶인 정수 또는 문자열이어야 합니다.

1. **대화 상자 제목에 따옴표 붙은 문자열이 필요 합니다.**

   `captiontext` DIALOG **문의 CAPTION 옵션에 있는** 필드는 큰따옴표로 묶인 ASCII 문자열이어야 합니다.

1. **파일을 찾을 수 없음: 파일 이름**

   리소스 컴파일러 명령줄에 지정된 파일을 찾을 수 없습니다. 파일이 다른 디렉터리로 이동되고 파일 이름 또는 경로가 올바르게 입력되었는지 확인합니다. 사용 가능한 경우 **INCLUDE** 환경 변수 또는 Visual Studio 설정을 사용 하 여 파일을 검색 합니다.

1. **글꼴 이름은 서 수 여야 합니다.**

   FONT 문의 *font 문의 pointsize* 필드는 문자열이 아닌 정수 여야 합니다.

1. **잘못 된 액셀러레이터**

   `event` ACCELERATORS **문의** 필드가 인식되지 않았거나 3자 이상입니다.

1. **잘못 된 액셀러레이터 유형 (ASCII 또는 VIRTKEY)**

   `type` ACCELERATORS **문의** 필드는 ASCII 또는 VIRTKEY 값을 포함해야 합니다.

1. **잘못 된 제어 문자**

   **ACCELERATORS** 문의 제어 문자가 잘못되었습니다. 유효한 제어 문자는 캐럿 (^) 뒤에 한 문자 (만)로 구성 됩니다.

1. **컨트롤 형식이 잘못 되었습니다.**

   **DIALOG** 문의 각 제어 문은 CHECKBOX, COMBOBOX, CONTROL, CTEXT, DEFPUSHBUTTON, EDITTEXT, GROUPBOX, ICON, LISTBOX, LTEXT, 누름, RADIOBUTTON, RTEXT, SCROLLBAR 중 하나 여야 합니다. 이러한 제어 문의 철자가 올바른지 확인 합니다.

1. **잘못 된 형식**

   리소스 형식이 WINDOWS .h 파일에 정의 된 형식에 속하지 않습니다.

1. **컨트롤에 텍스트 문자열 또는 서 수가 필요 합니다.**

   **DIALOG** 문에서 **control** 문의 *text* 필드는 컨트롤의 형식에 대 한 서 수 참조 또는 텍스트 문자열 이어야 합니다. 서수를 사용하는 경우 컨트롤을 위한 `#define` 문이 있는지 확인합니다.

1. **괄호가 일치 하지 않습니다.**

   **DIALOG** 문에서 모든 여는 괄호를 닫았는지 확인 합니다.

1. **RCData에 예기치 않은 값이 있습니다.**

   *RCDATA* 문의 **raw-data** 값은 각각 쉼표로 구분된 정수 또는 문자열이어야 합니다. 쉼표를 빠뜨렸거나 문자열 주위의 따옴표를 빠뜨리지 않았는지 확인합니다.

1. **알 수 없는 메뉴 하위 유형**

   **MENU** 문의 *항목 정의* 필드에는 **MENUITEM** 및 **POPUP** 문만 포함 될 수 있습니다.
