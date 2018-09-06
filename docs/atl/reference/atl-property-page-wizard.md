---
title: ATL 속성 페이지 마법사 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.ppg.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding property pages
- ATL Property Page Wizard
ms.assetid: 6113e325-facd-4f68-b491-144d75209922
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94bca969b150718450da166501abaea9c89b75d7
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760385"
---
# <a name="atl-property-page-wizard"></a>ATL 속성 페이지 마법사

이 마법사 [ATL 프로젝트에 속성 페이지 추가](../../atl/reference/adding-an-atl-property-page.md) 또는 MFC 프로젝트에 ATL 지원 합니다. 속성을 설정 하는 것에 대 한 사용자 인터페이스를 제공 하는 ATL 속성 페이지 (또는 메서드를 호출) 하나 이상의 COM 개체입니다.

## <a name="remarks"></a>설명

Visual Studio 2008부터,이 마법사에서 생성 된 등록 스크립트 등록에서 COM 구성 요소 **HKEY_CURRENT_USER** of **HKEY_LOCAL_MACHINE**합니다. 이 동작을 수정 하려면 설정 합니다 **모든 사용자에 대 한 구성 요소 등록** ATL 마법사의 옵션입니다.

## <a name="names"></a>이름

개체, 인터페이스 및 프로젝트에 추가할 클래스에 대 한 이름을 지정 합니다. 제외한 **약식 이름**, 다른 상자를 모두 독립적으로 편집할 수 있습니다. 에 대 한 텍스트를 변경 하면 **약식 이름**,이 페이지에 있는 다른 모든 상자의 이름에는 변경 내용이 반영 됩니다. 변경 하는 경우는 **Coclass** COM 섹션에서는 변경 이름에 반영 됩니다 합니다 **형식** 및 **ProgID** 상자입니다. 이 명명 문제는 모든 이름을 쉽게 식별할 수 있도록 사용자에 대 한 속성 페이지를 개발 하는 경우 설계 되었습니다.

> [!NOTE]
>  **Coclass** 하지 않는 프로젝트 에서만 편집할 수 있습니다. 프로젝트에서 특성을 사용 하는 경우 편집할 수 없습니다 **Coclass**합니다.

### <a name="c"></a>C++

개체를 구현 하기 위해 생성 하는 c + + 클래스에 대 한 정보를 제공 합니다.

|||
|-|-|
|용어|정의|
|**짧은 이름**|개체에 대 한 약식된 이름을 설정합니다. 클래스를 확인 하는 사용자가 제공한 이름 및 **Coclass** 이름, 파일 (**.cpp** 및 **.h**) 이름에는 **형식** 이름과 합니다  **ProgID**개별적으로 해당 필드를 변경 하지 않는 한, 합니다.|
|**.h 파일**|새 개체 클래스에 대한 헤더 파일의 이름을 설정합니다. 기본적으로이 이름은에서 제공 하는 이름에 기반 **약식 이름**합니다. 파일 이름을 선택한 위치에 저장하거나 클래스 선언을 기존 파일에 추가하려면 줄임표 단추를 클릭합니다. 기존 파일을 선택 하면 마법사 파일이 저장 되지 것입니다 선택한 위치에 때까지 클릭 **완료** 마법사에서.<br /><br /> 마법사는 파일을 덮어쓰지 않습니다. 기존 파일의 이름을 선택하면 마법사에서 **마침**을 클릭할 때 클래스 선언을 파일의 내용에 추가해야 하는지 여부를 나타내는 메시지가 표시됩니다. **예**를 클릭하여 파일을 추가하거나, **아니요**를 클릭하여 마법사로 돌아가서 다른 파일 이름을 지정합니다.|
|**클래스**|개체를 구현 하는 클래스의 이름을 설정 합니다. 이 이름은에서 제공 하는 이름에 기반 **약식 이름**클래스 이름에 대 한 일반적인 접두사 'C'가 뒤에서 합니다.|
|**.cpp 파일**|새 개체의 클래스에 대한 구현 파일의 이름을 설정합니다. 기본적으로이 이름은에서 제공 하는 이름에 기반 **약식 이름**합니다. 파일 이름을 선택한 위치에 저장하려면 줄임표 단추를 클릭합니다. 마법사에서 **마침**을 클릭해야 해당 파일이 선택한 위치에 저장됩니다.<br /><br /> 마법사는 파일을 덮어쓰지 않습니다. 기존 파일의 이름을 선택하면 마법사에서 **마침**을 클릭할 때 클래스 구현을 파일의 내용에 추가해야 하는지 여부를 나타내는 메시지가 표시됩니다. **예**를 클릭하여 파일을 추가하거나, **아니요**를 클릭하여 마법사로 돌아가서 다른 파일 이름을 지정합니다.|
|**특성 사용**|개체 특성을 사용 하는지 여부를 나타냅니다. 특성 사용된 ATL 프로젝트에 개체를 추가 하는이 옵션을 선택 하 고 변경할 수 없습니다, 즉, 추가할 수 있습니다만 인 한 개체 특성 지원을 사용 하 여 만든 프로젝트에 있습니다.<br /><br /> 특성 사용된 개체에서 특성을 사용 하는 ATL 프로젝트에만 추가할 수 있습니다. 특성을 지원 하지 않은 ATL 프로젝트에 대해이 옵션을 선택 하면 마법사 특성 지원 프로젝트에 추가할 것인지를 지정 하 라는 메시지를 표시 합니다.<br /><br /> 기본적으로이 옵션을 설정 하면 추가한 모든 개체 특성을 사용 하는 대로 지정 됩니다 (확인란 선택). 특성을 사용 하지 않는 개체를 추가 하려면이 상자를 지울 수 있습니다.<br /><br /> 참조 [ATL 프로젝트 마법사, 응용 프로그램 설정](../../atl/reference/application-settings-atl-project-wizard.md) 하 고 [특성의 기본 메커니즘](../../windows/basic-mechanics-of-attributes.md) 자세한 내용은 합니다.|

### <a name="com"></a>COM

개체에 대 한 COM 기능에 대 한 정보를 제공합니다.

**Coclass**  
개체에서 지 원하는 인터페이스의 목록을 포함 하는 구성 요소 클래스의 이름을 설정 합니다.

> [!NOTE]
>  특성을 사용 하 여 프로젝트를 만들거나 ATL 포함 되어 있지 않으므로이 옵션을 지정할 경우이 마법사 페이지에서 속성 페이지 특성을 사용 하는 변경할 수 없습니다는 `coclass` 특성입니다.

**Type**  
레지스트리에 나타나는 개체 설명 설정

**ProgID**  
컨테이너 개체의 CLSID 대신 사용할 수 있는 이름을 설정 합니다.

## <a name="see-also"></a>참고 항목

[옵션, ATL 속성 페이지 마법사](../../atl/reference/options-atl-property-page-wizard.md)   
[문자열, ATL 속성 페이지 마법사](../../atl/reference/strings-atl-property-page-wizard.md)   
[예: 속성 페이지 구현](../../atl/example-implementing-a-property-page.md)

