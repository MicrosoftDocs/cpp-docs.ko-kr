---
description: '방법에 대 한 자세한 정보: 방법: 기호 만들기 (c + +)'
title: '방법: 기호 만들기 (c + +)'
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
ms.openlocfilehash: 961c186796e239471507b83dc301186d05004800
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329470"
---
# <a name="how-to-create-symbols-c"></a>방법: 기호 만들기 (c + +)

새 프로젝트를 시작 하는 경우 할당 되는 리소스를 만들기 전에 필요한 기호 이름을 매핑하는 것이 편리할 수 있습니다.

> [!NOTE]
> 프로젝트에 .rc 파일이 아직 없는 경우 [방법: 리소스 만들기](../windows/how-to-create-a-resource-script-file.md)를 참조 하세요.

**리소스 기호** 대화 상자를 사용 하 여 새 리소스 기호를 추가 하거나, 표시 되는 기호를 변경 하거나, 소스 코드에서 기호가 사용 되는 위치로 건너뛸 수 있습니다.

이 대화 상자에는 다음과 같은 속성이 있습니다.

|속성|설명|
|--------------------------|------------------------------------------|
|**이름**|기호의 이름을 표시합니다.<br/><br/>자세한 내용은 [기호 이름 제한](./changing-a-symbol-or-symbol-name-id.md)을 참조 하세요.|
|**값**|기호의 숫자 값을 표시합니다.<br/><br/>자세한 내용은 [기호 값 제한](./changing-a-symbol-or-symbol-name-id.md)을 참조 하세요.|
|**사용 중인**|선택하면 하나 이상의 리소스에서 기호를 사용하고 있음을 지정합니다.<br/><br/>리소스는 **사용 된 사람** 상자에 나열 됩니다.|
|**읽기 전용 기호 표시**|선택하면 읽기 전용 리소스를 표시합니다.<br/><br/>기본적으로 **리소스 기호** 대화 상자는 리소스 스크립트 파일에 수정 가능한 리소스만 표시 하지만이 옵션을 선택 하면 수정 가능한 리소스가 굵은 텍스트로 표시 되 고 읽기 전용 리소스가 일반 텍스트로 표시 됩니다.|
|**사용 된 사람**|기호 목록에서 선택한 기호를 사용하여 리소스를 표시합니다.<br/><br/>지정 된 리소스에 대 한 편집기로 이동 하려면 **사용** 상자에서 리소스를 선택 하 고 **사용 보기** 를 선택 합니다.|
|**새로 만들기**|새 기호화 된 리소스 식별자에 대 한 이름 및 필요한 경우 값을 정의할 수 있는 **새 기호** 대화 상자를 엽니다.|
|**변경**|기호의 이름 또는 값을 변경할 수 있는 **기호 변경** 대화 상자를 엽니다.<br/><br/>사용 중인 컨트롤 또는 리소스에 대한 기호인 경우 해당 리소스 편집기에서만 기호를 변경할 수 있습니다. 자세한 내용은 [기호 관리](./changing-a-symbol-or-symbol-name-id.md)를 참조 하세요.|
|**사용 리소스 보기**|해당 리소스 편집기에서 기호를 포함하는 리소스를 엽니다.|

## <a name="create-symbols"></a>기호 만들기

### <a name="to-create-a-new-symbol"></a>새 기호를 만들려면

1. **리소스 기호** 대화 상자에서 **새로 만들기** 를 선택 합니다.

1. **이름** 상자에 기호 이름을 입력 합니다.

1. 할당 된 기호 값을 그대로 적용 하거나 **값** 상자에 새 값을 입력 합니다.

1. **확인** 을 선택 하 여 기호 목록에 새 기호를 추가 합니다.

> [!NOTE]
> 이미 있는 기호 이름을 입력하면 해당 이름을 사용하는 기호가 이미 정의되어 있다는 메시지 상자가 나타납니다. 같은 이름으로 두 개 이상의 기호를 정의할 수는 없지만 동일한 숫자 값을 사용 하 여 다른 기호를 정의할 수는 있습니다.

## <a name="to-view-resource-symbols"></a>리소스 기호를 보려면

[리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 *.rc* 파일을 마우스 오른쪽 단추로 클릭 하 **고 리소스 기호를 선택 하** 여 리소스 **기호** 대화 상자에서 리소스 기호 테이블을 확인 합니다.

> [!NOTE]
> 미리 정의 된 기호를 보려면 **읽기 전용 기호 표시** 확인란을 선택 합니다.

### <a name="to-open-the-resource-editor-for-a-given-symbol"></a>지정 된 기호에 대 한 리소스 편집기를 열려면

**리소스 기호** 에서 기호를 검색 하는 경우 특정 기호를 사용 하는 방법에 대 한 자세한 정보를 볼 수 있습니다. **보기 사용** 단추를 사용 하 여이 정보를 신속 하 게 가져올 수 있습니다.

1. **리소스 기호** 대화 상자의 **이름** 상자에서 기호를 선택 합니다.

1. 사용 된 **사람** 상자에서 관심 있는 리소스 종류를 선택 합니다.

1. **보기 사용** 단추를 선택 합니다.

   리소스가 해당 편집기 창에 나타납니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[리소스 식별자 (기호)](../windows/symbols-resource-identifiers.md)<br/>
[방법: 기호 관리](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[미리 정의 된 기호 Id](../windows/predefined-symbol-ids.md)<br/>
