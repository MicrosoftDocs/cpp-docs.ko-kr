---
description: '자세히 알아보기: 방법: 대화 상자 만들기 (c + +)'
title: '방법: 대화 상자 만들기 (c + +)'
ms.date: 02/15/2019
helpviewer_keywords:
- dialog boxes [C++], creating
- Dialog Editor [C++], creating dialog boxes
- modal dialog boxes [C++], logon screens
- logon screens
- Test Dialog command
- testing, dialog boxes
- dialog boxes [C++], testing
- dialog boxes [C++], size
- dialog boxes [C++], positioning
ms.assetid: 303de801-c4f8-42e1-b622-353f6423f688
ms.openlocfilehash: 8c02d0d85d20b51c867b3f3ba0e5f945595ed130
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329490"
---
# <a name="how-to-create-a-dialog-box-c"></a>방법: 대화 상자 만들기 (c + +)

C + + 대화 상자의 위치 및 크기와 그 안에 포함 된 컨트롤의 위치와 크기는 대화 상자 단위로 측정 됩니다. 개별 컨트롤의 값과 대화 상자를 선택 하면 Visual Studio 상태 표시줄의 오른쪽 아래에 해당 값이 표시 됩니다.

> [!NOTE]
> 프로젝트에 .rc 파일이 아직 없는 경우 [새 리소스 스크립트 파일 만들기](../windows/how-to-create-a-resource-script-file.md)를 참조 하세요.

## <a name="how-to"></a>방법

**대화 상자 편집기** 를 사용 하 여 다음을 수행할 수 있습니다.

### <a name="to-create-a-new-dialog-box"></a>새 대화 상자를 만들려면

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 *.rc* 파일을 마우스 오른쪽 단추로 클릭 하 고 **리소스 추가** 를 선택 합니다.

1. **리소스 추가** 대화 상자의 **리소스 종류** 목록에서 **대화** 상자를 선택한 다음 **새로 만들기** 를 선택 합니다.

   **+** **대화** 상자 리소스 유형 옆에 더하기 기호 ()가 나타나면 대화 상자 템플릿을 사용할 수 있음을 의미 합니다. 더하기 기호를 선택 하 여 템플릿 목록을 확장 하 고, 템플릿을 선택 하 고, **새로 만들기** 를 선택 합니다.

   새 대화 상자가 **대화 상자 편집기** 에서 열립니다.

편집을 위해 대화 상자 편집기에서 기존 대화 상자를 열 수도 있습니다.

### <a name="to-create-a-dialog-box-that-a-user-cant-exit"></a>사용자가 종료할 수 없는 대화 상자를 만들려면

사용자가 종료할 수 없는 런타임 대화 상자를 만들 수 있습니다. 이 종류의 대화 상자는 로그온에 유용하며, 애플리케이션 또는 문서를 잠그는 데에도 유용합니다.

1. 대화 상자의 **속성** 창에서 **시스템 메뉴** 속성을로 설정 **`false`** 합니다.

   이 설정은 대화 상자 시스템 메뉴 및 **닫기** 단추를 사용 하지 않도록 설정 합니다.

1. 대화 상자 폼에서 **취소** 및 **확인** 단추를 삭제합니다.

   런타임에 사용자는 이러한 특징이 있는 모달 대화 상자를 종료할 수 없습니다.

이러한 종류의 대화 상자를 테스트할 수 있도록 테스트 대화 상자 함수는 **Esc 키** 를 누를 때 검색 합니다. **Esc** 는 VK_ESCAPE 가상 키 라고도 합니다. 대화 상자가 런타임에 동작 하도록 디자인 된 방법에 관계 없이 **Esc** 키를 눌러 테스트 모드를 종료할 수 있습니다.

> [!NOTE]
> MFC 응용 프로그램의 경우 사용자가 종료할 수 없는 대화 상자를 만들려면 및의 기본 동작을 재정의 해야 `OnOK` 합니다 `OnCancel` . 관련 된 단추를 삭제 하더라도 **enter** 또는 **Esc** 키를 누르면 대화 상자를 닫을 수 있기 때문입니다.

### <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>대화 상자의 위치와 크기를 지정 하려면

대화 상자가 화면에 표시 되는 위치를 지정 하기 위해 [속성 창](/visualstudio/ide/reference/properties-window) 에서 설정할 수 있는 속성이 있습니다.

- 부울 **중심** 속성입니다.

   값을 **True** 로 설정 하면 대화 상자는 항상 화면 가운데에 표시 됩니다. 이 속성을 **False** 로 설정 하면 **XPos** 및 **YPos** 속성을 설정할 수 있습니다.

- 대화 상자 화면에 표시 되는 위치를 명시적으로 정의 하는 데 사용 되는 **XPos** 및 **YPos** 속성

   이러한 위치 속성은로 정의 되는 보기 영역의 왼쪽 위 모퉁이에서 오프셋 값입니다 `{X=0, Y=0}` .

- 위치에 영향을 주는 **절대 맞춤** 속성입니다.

   **True** 이면 좌표는 화면을 기준으로 합니다. **False** 이면 좌표가 대화 상자의 소유자 창에 상대적입니다.

### <a name="to-test-a-dialog-box"></a>대화 상자를 테스트하려면

대화 상자를 디자인할 때 프로그램을 컴파일하지 않고 런타임에 동작을 시뮬레이션 및 테스트할 수 있습니다. 이 모드에서 다음 작업을 수행할 수 있습니다.

- 텍스트 입력, 콤보 상자 목록에서 선택, 옵션 켜기 또는 끄기, 명령 선택

- 탭 순서 테스트

- 라디오 단추 또는 확인란과 같은 컨트롤의 그룹화 테스트

- 대화 상자의 컨트롤에 대한 바로가기 키 테스트

> [!NOTE]
> 마법사를 사용 하 여 만든 대화 상자 코드에 대 한 연결은 시뮬레이션에 포함 되지 않습니다.

대화 상자를 테스트할 때는 일반적으로 주 프로그램 창을 기준으로 상대적인 위치에 표시됩니다. 대화 상자 **절대값** 속성을 **True** 로 설정한 경우 대화 상자는 화면의 왼쪽 위 모퉁이를 기준으로 하는 위치에 표시 됩니다.

1. **대화 상자 편집기** 가 활성 창이 면 메뉴 **형식**  >  **테스트 대화 상자로** 이동 합니다.

1. 시뮬레이션을 종료 하려면 **Esc** 키를 누르거나 테스트 하는 대화 상자에서 **닫기** 단추를 선택 합니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[대화 상자 편집기](../windows/dialog-editor.md)<br/>
[방법: 대화 상자 컨트롤 관리](../windows/controls-in-dialog-boxes.md)<br/>
