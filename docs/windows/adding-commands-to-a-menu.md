---
title: (C + +) 메뉴에 명령 추가 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.menu
dev_langs:
- C++
helpviewer_keywords:
- menu items, adding to menus
- menus [C++], adding items
- commands [C++], adding to menus
ms.assetid: 1523a755-0ab5-42f8-9e98-bb9881564431
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 852d91dc6bc72fc86307199c8d2e7b67d53323bc
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50057649"
---
# <a name="adding-commands-to-a-menu-c"></a>(C + +) 메뉴에 명령 추가

### <a name="to-add-commands-to-a-menu"></a>메뉴에 명령을 추가하려면

1. [메뉴 만들기](../windows/creating-a-menu.md)합니다.

2. 예를 들어 메뉴 이름을 클릭 **파일**합니다.

   각 메뉴가 확장되고 명령에 대한 새 항목 상자가 표시됩니다. 예를 들어 명령을 추가할 수 있습니다 **새로 만들기**, **열려**, 및 **닫기** 하는 **파일** 메뉴.

3. 새 항목 상자에 새 메뉴 명령에 대한 이름을 입력합니다.

   > [!NOTE]
   > 입력하는 텍스트는 **메뉴** 편집기와 **속성 창** 의 [캡션](/visualstudio/ide/reference/properties-window)상자에 모두 나타납니다. 한 위치에서 새 메뉴에 대한 속성을 편집할 수 있습니다.

   > [!TIP]
   > 사용자가 메뉴 명령을 선택할 수 있도록 니모닉 키(바로 가기 키)를 정의할 수 있습니다. 앰퍼샌드를 입력 (`&`) 니모닉으로 지정 하려면 문자 앞에 있습니다. 사용자는 해당 문자를 입력하여 메뉴 명령을 선택할 수 있습니다.

4. 에 **속성** 창에서 메뉴 명령을 적용 되는 속성입니다. 자세한 내용은 참조 하세요 [메뉴 명령 속성](../windows/menu-command-properties.md)합니다.

5. 에 **프롬프트** 상자에 **속성** 창 응용 프로그램의 상태 표시줄에 표시할 프롬프트 문자열을 입력 합니다.

   이렇게 하면 앞에서 만든 메뉴 명령과 동일한 리소스 식별자를 사용하는 항목이 문자열 테이블에 만들어집니다.

   > [!NOTE]
   > 프롬프트 메뉴 항목에만 적용할 수는 **팝업** 속성을 **True**합니다. 예를 들어 최상위 메뉴 항목은 하위 메뉴 항목이 있는 경우 프롬프트가 적용됩니다. 용도 **프롬프트** 어떤 동작이 발생 했다는 것을 사용자가 메뉴 항목을 클릭 합니다.

6. 키를 눌러 **Enter** 메뉴 명령을 완료 합니다.

   새 항목 상자를 선택하여 추가 메뉴 명령을 만들 수 있습니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[메뉴 편집기](../windows/menu-editor.md)