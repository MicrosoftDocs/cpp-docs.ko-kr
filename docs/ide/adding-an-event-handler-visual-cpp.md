---
title: 이벤트 처리기 추가
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.eventhandler.overview
helpviewer_keywords:
- event handlers, adding
- properties [Visual Studio], MSBuild
- MSBuild, properties
- event handler wizard [C++]
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
ms.openlocfilehash: b1928de1aacb9c66c9f784f4eee41ce2c444b820
ms.sourcegitcommit: 6284bca6549e7b4f199d4560c30df6c1278bd4a0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96188941"
---
# <a name="add-an-event-handler"></a>이벤트 처리기 추가

리소스 편집기에서 [이벤트 처리기 마법사](#event-handler-wizard)를 사용하여 대화 상자 컨트롤에 대해 새 이벤트 처리기를 추가하거나 기존 이벤트 처리기를 편집할 수 있습니다.

[속성 창](/visualstudio/ide/reference/properties-window)을 사용하여 대화 상자를 구현하는 클래스에 이벤트를 추가할 수 있습니다. 대화 상자 클래스 이외의 다른 클래스에 이벤트를 추가하려면 이벤트 처리기 마법사를 사용합니다.

**대화 상자 컨트롤에 이벤트 처리기를 추가하려면:**

1. [리소스 뷰](../windows/how-to-create-a-resource-script-file.md#create-resources)에서 대화 상자 리소스를 두 번 클릭하여 [대화 상자 편집기](../windows/dialog-editor.md)의 컨트롤이 포함된 대화 상자 리소스를 엽니다.

1. 알림 이벤트를 처리할 컨트롤을 마우스 오른쪽 단추로 클릭합니다.

1. 바로 가기 메뉴에서 **이벤트 처리기 추가** 를 선택하여 이벤트 처리기 마법사를 표시합니다.

1. **메시지 유형** 상자에서 이벤트를 선택하여 **클래스 목록** 상자에서 선택한 클래스를 추가합니다.

1. **함수 처리기 이름** 상자에서 기본 이름을 수락하거나 원하는 이름을 제공합니다.

1. **추가 및 편집** 을 선택하여 이벤트 처리기를 프로젝트에 추가하고, 새 함수에서 텍스트 편집기를 열어 적절한 이벤트 처리기 코드를 추가합니다.

   선택한 메시지 유형에 선택한 클래스에 대한 이벤트 처리기가 이미 있는 경우, **추가 및 편집** 을 사용할 수 없고 **코드 편집** 을 사용할 수 있습니다. **코드 편집** 을 선택하여 기존 함수에서 텍스트 편집기를 엽니다.

또는 [속성 창](/visualstudio/ide/reference/properties-window)에서 이벤트 처리기를 추가할 수 있습니다. 자세한 내용은 [대화 상자 컨트롤에 대한 이벤트 처리기 추가](../windows/adding-editing-or-deleting-controls.md)를 참조하세요.

## <a name="in-this-section"></a>섹션 내용

- [이벤트 처리기 마법사](#event-handler-wizard)

## <a name="event-handler-wizard"></a>이벤트 처리기 마법사

이 마법사는 대화 상자 컨트롤에 대한 이벤트 처리기를 선택한 클래스에 추가합니다. [속성 창](/visualstudio/ide/reference/properties-window)에서 이벤트 처리기를 추가하는 경우 대화 상자를 구현하는 클래스에만 추가할 수 있습니다. 자세한 내용은 [대화 상자 컨트롤에 대한 이벤트 처리기 추가](../windows/adding-editing-or-deleting-controls.md)를 참조하세요.

- **명령 이름**

  이벤트 처리기를 추가하는 것에 대해 선택한 컨트롤을 식별합니다. 이 상자를 사용할 수 없습니다.

- **메시지 유형**

  선택한 컨트롤에 대한 현재 가능한 메시지 처리기 목록을 표시합니다.

- **함수 처리기 이름**

  이벤트를 처리하기 위해 추가하는 함수 이름을 표시합니다. 기본적으로 이름은 `On`이 추가되는 메시지 유형 및 명령을 기반으로 합니다. 예를 들어 `IDC_BUTTON1`이라는 단추의 경우 메시지 유형 `BN_CLICKED`는 함수 처리기 이름 `OnBnClickedButton1`을 표시합니다.

- **클래스 목록**

  이벤트 처리기를 추가할 수 있는 사용가능한 클래스를 표시합니다. 선택한 대화 상자의 클래스는 빨간색으로 표시됩니다.

- **처리기 설명**

  **메시지 유형** 상자에서 선택한 항목에 대한 설명을 제공합니다. 이 상자를 사용할 수 없습니다.

- **추가 및 편집**

  선택한 클래스 또는 개체에 메시지 처리기를 추가합니다. 또한 컨트롤 알림에 처리기 코드를 추가할 수 있도록 새 함수에 대한 텍스트 편집기를 엽니다.

- **코드 편집**

  컨트롤 알림 처리기 코드를 추가하거나 편집할 수 있도록 선택한 기존 함수에서 텍스트 편집기를 엽니다.
