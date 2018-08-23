---
title: 컨트롤의 탭 순서 변경 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], tab order
- focus, tab order
- tab controls, tab order
- Tabstop property for controls
- controls [C++], focus
- dialog box controls, tab order
ms.assetid: e2cee764-4367-42d7-9563-65a68f76f5ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f5f846244956687b73b6fc7272fe0c4d7d00d0e0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596343"
---
# <a name="changing-the-tab-order-of-controls"></a>컨트롤의 탭 순서 변경

탭 순서는 순서를 **탭** 키 대화 상자 내에서 다음 컨트롤에서 입력된 포커스를 이동 합니다. 일반적으로 탭 순서는 왼쪽에서 오른쪽, 위쪽에서 대화 상자에서 아래쪽으로 진행 됩니다. 각 컨트롤에는 **Tabstop** 컨트롤에 입력 포커스가 있는지 여부를 결정 하는 속성입니다.

### <a name="to-set-input-focus-for-a-control"></a>컨트롤에 대 한 입력된 포커스를 설정 하려면

1. 에 [속성 창](/visualstudio/ide/reference/properties-window)를 선택 **True** 또는 **False** 에 **Tabstop** 속성입니다.

없는 컨트롤을 **Tabstop** 속성이로 설정 **True** 탭 순서의 일부가 되도록 해야 합니다. 이 중요할 수 있습니다, 예를 들어 경우 있습니다 [액세스 키 (니모닉) 정의](../windows/defining-mnemonics-access-keys.md) 캡션이 없는 컨트롤에 대 한 합니다. 관련된 컨트롤에 대 한 액세스 키를 포함 하는 정적 텍스트 바로 앞에 나와야 관련된 컨트롤 탭 순서에서입니다.

> [!NOTE]
> 겹치는 컨트롤을 포함 하는 대화 상자에서 탭 순서 변경 컨트롤이 표시 되는 방식을 변경할 수 있습니다. 탭 순서에서 나중에 제공 되는 컨트롤은 항상 탭 순서에서 앞에 겹치는 컨트롤 위에 표시 됩니다.

### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>대화 상자에서 모든 컨트롤에 대 한 현재 탭 순서를 보려면

1. 에 **형식** 메뉴에서 클릭 **탭 순서**합니다.

\- 또는 -

- 키를 눌러 **Ctrl**+**D**합니다.

### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>대화 상자에서 모든 컨트롤에 대 한 탭 순서를 변경 하려면

1. 에 **형식** 메뉴에서 클릭 **탭 순서**합니다.

   각 컨트롤의 왼쪽 위 모서리에 있는 숫자로 현재 탭 순서에서 해당 위치를 보여 줍니다.

2. 원하는 순서 대로 각 컨트롤을 클릭 하 여 탭 순서를 설정 합니다 **탭** 키에 따라 합니다.

3. 키를 눌러 **Enter** 끝내려면 **탭 순서** 모드입니다.

   > [!TIP]
   > 입력 한 후 **탭 순서** 모드를 눌러도 **Esc** 또는 **Enter** 탭 순서를 변경 하는 기능을 사용 하지 않도록 설정 합니다.

### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>두 개 이상 컨트롤의 탭 순서를 변경 하려면

1. **형식** 메뉴 선택 **탭 순서**합니다.

2. 순서 변경을 시작 위치를 지정 합니다. 이 작업을 수행 하려면 누른 합니다 **Ctrl** 키 및 시작에 대 한 변경된 하려면 원하는 전에 컨트롤을 클릭 합니다.

   예를 들어, 컨트롤의 순서를 변경 하려는 경우 `7` 를 통해 `9`를 누른 **Ctrl**를 한 컨트롤을 선택 `6` 첫 번째입니다.

   > [!NOTE]
   > 특정 컨트롤 번호를 설정 하려면 `1` (탭 순서)에서 첫 번째 컨트롤을 두 번 클릭 합니다.

3. 릴리스를 **Ctrl** 원하는 순서 대로 컨트롤을 클릭 한 다음 키를 **탭** 해당 지점에서 수행 하는 키입니다.

4. 키를 눌러 **Enter** 끝내려면 **탭 순서** 모드입니다.

관리 되는 프로젝트에 리소스를 추가 하는 방법에 대 한 정보를 참조 하세요 [데스크톱 앱의 리소스](/dotnet/framework/resources/index) 에 *.NET Framework Developer's Guide*합니다. 수동으로 관리 되는 프로젝트에 리소스 파일을 추가, 리소스 액세스, 정적 리소스 표시 및 속성에 리소스 문자열 할당에 대 한 내용은 참조 하세요 [데스크톱 앱에 대 한 리소스 파일 만들기](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)합니다. 전역화 및 지역화 관리 되는 앱의 리소스에 대 한 내용은 참조 하세요 [Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)합니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[대화 상자에 컨트롤 배치](../windows/arrangement-of-controls-on-dialog-boxes.md)  
[대화 상자의 컨트롤](../windows/controls-in-dialog-boxes.md)  
[컨트롤](../mfc/controls-mfc.md)