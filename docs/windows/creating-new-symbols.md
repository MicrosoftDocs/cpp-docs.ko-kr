---
title: '방법: 기호 (c + +) 만들기'
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.creating
- vc.editors.symbol.managing
- vc.editors.resourcesymbols
- vc.editors.symbol.resource
helpviewer_keywords:
- New Symbol dialog box [C++]
- symbols [C++], creating
- resources [C++], viewing
- resource symbols
- symbols [C++], viewing
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
- resource symbols
- View Use button
- resource editors [C++], resource symbols
ms.assetid: 35168d31-3af6-4ecd-9362-3707d47b53f3
ms.openlocfilehash: 01b810d162da4d59c2044fe02a1da5c0929d41b9
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320603"
---
# <a name="how-to-create-symbols-c"></a>방법: 기호 (c + +) 만들기

새 프로젝트를 시작 하는 경우 있습니다 됩니다 수 할당 된 리소스를 만들기 전에 필요한 기호 이름을 매핑하는 것이 편리할 수 있습니다.

합니다 **리소스 기호** c + + 대화 상자를 사용 하면 새 리소스 기호 추가을 기호를 사용에서 하는 소스 코드의 위치를 건너뛸지 표시 되는 기호를 변경 합니다.

대화 상자에는 다음 속성이 포함 됩니다.

|속성|설명|
|--------------------------|------------------------------------------|
|**이름**|기호의 이름을 표시합니다. 자세한 내용은 [기호 이름 제한](../windows/symbol-name-restrictions.md)합니다.|
|**값**|기호의 숫자 값을 표시합니다. 자세한 내용은 [기호 값 제한](../windows/symbol-value-restrictions.md)합니다.|
|**사용**|선택하면 하나 이상의 리소스에서 기호를 사용하고 있음을 지정합니다. 해당 리소스가 다음에서 사용 상자에 나열됩니다.|
|**읽기 전용 기호 표시**|선택하면 읽기 전용 리소스를 표시합니다. 기본적으로 **리소스 기호** 대화 상자 리소스 스크립트 파일의 수정 가능한 리소스만 표시 되지만이 옵션을 선택 하면 수정할 수 있는 리소스 굵은 텍스트로 표시 되 고 읽기 전용 리소스 일반 텍스트로 표시 합니다.|
|**사용 하는**|기호 목록에서 선택한 기호를 사용하여 리소스를 표시합니다. 지정된 된 리소스에 대 한 편집기로 이동 하려면에서 리소스를 선택 하는 **Used By** 확인란을 선택한 **사용 리소스 보기**합니다.|
|**새로 만들기**|열립니다는 **새 기호** 이름을 정의 하는 대화 상자 및 필요한 경우 새 기호화 된 리소스 식별자에 대 한 값입니다.|
|**Change**|열립니다는 **기호 변경** 대화 상자를 이름 또는 기호 값을 변경할 수 있습니다. 사용 중인 컨트롤 또는 리소스에 대한 기호인 경우 해당 리소스 편집기에서만 기호를 변경할 수 있습니다. 자세한 내용은 [할당 되지 않은 기호 변경](../windows/changing-unassigned-symbols.md)합니다.|
|**사용 리소스 보기**|해당 리소스 편집기에서 기호를 포함하는 리소스를 엽니다.|

## <a name="create-symbols"></a>기호 만들기

### <a name="to-create-a-new-symbol"></a>새 기호를 만들려면

1. 에 **리소스 기호** 대화 상자에서 **새로 만들기**합니다.

1. 에 **이름을** 상자 기호 이름을 입력 합니다.

1. 할당 된 기호 값을 그대로 사용 하거나 새 값을 입력 합니다 **값** 상자입니다.

1. 선택 **확인** 기호 목록에 새 기호를 추가 합니다.

> [!NOTE]
> 이미 있는 기호 이름을 입력하면 해당 이름을 사용하는 기호가 이미 정의되어 있다는 메시지 상자가 나타납니다. 이름이 같은 기호를 두 개 이상 정의할 수는 없지만 동일한 숫자 값을 사용하는 서로 다른 기호는 정의할 수 있습니다. 자세한 내용은 [기호 이름 제한](../windows/symbol-name-restrictions.md) 하 고 [기호 값 제한](../windows/symbol-value-restrictions.md)합니다.

### <a name="to-view-resource-symbols"></a>리소스 기호를 보려면

1. [리소스 뷰](../windows/resource-view-window.md),.rc 파일을 마우스 오른쪽 단추로 클릭 합니다.

   > [!NOTE]
   > 프로젝트에 .rc 파일이 아직 없는 경우 [새 리소스 스크립트 파일 만들기](../windows/how-to-create-a-resource-script-file.md)를 참조하세요.

1. 선택 **리소스 기호** 에서 리소스 기호 테이블을 보려면 바로 가기 메뉴에서의 **리소스 기호** 대화 상자.

   > [!NOTE]
   > 미리 정의 된 기호를 확인 합니다 **읽기 전용 기호 표시** 확인란 합니다.

### <a name="to-open-the-resource-editor-for-a-given-symbol"></a>지정된 된 기호에 대 한 리소스 편집기를 열려면

기호를 검색 하는 경우는 **리소스 기호**, 특정 기호를 사용 하는 방법에 대 한 자세한 내용은 확인할 수 있습니다. 합니다 **사용 리소스 보기** 단추에는이 정보를 얻으려면 빠른 방법을 제공 합니다.

#### <a name="to-move-to-the-resource-editor-where-a-symbol-is-being-used"></a>기호가 사용되는 리소스 편집기로 이동하려면

1. 기호를 선택 합니다 **이름을** 상자를 **리소스 기호** 대화 상자.

1. 에 **Used By** 상자에서 관심 있는 리소스 종류를 선택 합니다.

1. 선택 된 **사용 리소스 보기** 단추입니다.

   리소스가 해당 편집기 창에 나타납니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[리소스 식별자 (기호)](../windows/symbols-resource-identifiers.md)<br/>
[기호 관리](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[미리 정의된 기호 ID](../windows/predefined-symbol-ids.md)<br/>