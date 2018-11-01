---
title: 테스트 대화 상자 (c + +)
ms.date: 11/04/2016
helpviewer_keywords:
- Test Dialog command
- testing, dialog boxes
- dialog boxes [C++], testing
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
ms.openlocfilehash: 101a2b556b2593953bfa6482f96d5b1aadc38d1c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625068"
---
# <a name="testing-a-dialog-box-c"></a>테스트 대화 상자 (c + +)

대화 상자를 디자인할 때 프로그램을 컴파일하지 않고 런타임에 동작을 시뮬레이션 및 테스트할 수 있습니다. 이 모드에서 다음 작업을 수행할 수 있습니다.

- 텍스트 입력, 콤보 상자 목록에서 선택, 옵션 켜기 또는 끄기, 명령 선택

- 탭 순서 테스트

- 라디오 단추 또는 확인란과 같은 컨트롤의 그룹화 테스트

- 대화 상자의 컨트롤에 대한 바로가기 키 테스트

   > [!NOTE]
   > 마법사를 사용하여 만든 대화 상자 코드에 대한 연결은 시뮬레이션에 포함되지 않습니다.

대화 상자를 테스트할 때는 일반적으로 주 프로그램 창을 기준으로 상대적인 위치에 표시됩니다. 대화 상자를 설정한 경우 **Absolute Align** 속성을 **True**를 화면의 왼쪽 위 모퉁이 기준으로 하는 위치에 있는 대화 상자에 표시 됩니다.

### <a name="to-test-a-dialog-box"></a>대화 상자를 테스트하려면

1. 경우는 **대화 상자** 편집기가 활성 창, 메뉴 모음에서 선택 합니다 **형식** > **테스트 대화 상자**합니다.

2. 시뮬레이션을 종료 하려면 키를 누릅니다 **Esc**를 선택 하거나 합니다 **닫기** 테스트 하는 대화 상자에서 단추입니다.

관리 되는 프로젝트에 리소스를 추가 하는 방법에 대 한 정보를 참조 하세요 [데스크톱 앱의 리소스](/dotnet/framework/resources/index)합니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[대화 상자의 컨트롤](../windows/controls-in-dialog-boxes.md)<br/>
[대화 상자 편집기](../windows/dialog-editor.md)<br/>
[대화 상자 편집기 도구 모음 표시 또는 숨기기](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)