---
description: '자세한 정보: ATL OLE DB 공급자 마법사'
title: ATL OLE DB 공급자 마법사
ms.date: 05/09/2019
helpviewer_keywords:
- ATL projects, adding ATL OLE DB providers
ms.assetid: cf91ba78-01d1-4d12-b673-e95d96bfbebe
ms.openlocfilehash: 068670205c45c559e8b312d633d715f51a78190d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165344"
---
# <a name="atl-ole-db-provider-wizard"></a>ATL OLE DB 공급자 마법사

::: moniker range="msvc-160"

Visual Studio 2019 이상에서는 이 마법사를 사용할 수 없습니다.

::: moniker-end

::: moniker range="<=msvc-150"

## <a name="remarks"></a>설명

Visual Studio 2008부터, 이 마법사에서 생성된 등록 스크립트는 해당 COM 구성 요소를 **HKEY_LOCAL_MACHINE** 대신 **HKEY_CURRENT_USER** 아래에 등록합니다. 이 동작을 수정하려면 ATL 마법사의 **모든 사용자에 대해 구성 요소 등록** 옵션을 설정합니다.

다음 표에서는 ATL OLE DB 공급자 마법사의 옵션을 보여 줍니다.

- **짧은 이름**

   만들어질 공급자의 짧은 이름을 입력합니다. 마법사의 다른 편집 상자는 여기서 입력한 내용에 따라 자동으로 채워집니다. 필요한 경우 다른 이름 상자를 편집할 수 있습니다.

- **Coclass**

   coclass의 이름입니다. 이 이름과 일치하도록 ProgID 이름이 변경됩니다.

- **특성 사용**

   이 옵션은 마법사에서 공급자 클래스를 만드는 데 특성을 사용할지 또는 템플릿 선언을 사용할지를 지정합니다. 이 옵션을 선택하면 템플릿 선언 대신 특성이 사용됩니다(특성 사용 프로젝트를 만든 경우 기본 옵션). 이 옵션의 선택을 취소하면 특성 대신 템플릿 선언이 사용됩니다(특성을 사용하지 않는 프로젝트를 만든 경우 기본 옵션).

   특성을 사용하지 않는 프로젝트를 만들었을 때 이 옵션을 선택하면 프로젝트가 특성 사용 프로젝트로 변환된다고 경고하고 계속할지 여부를 묻는 메시지가 표시됩니다.

- **ProgID**

   ProgID(프로그래밍 ID)는 애플리케이션에서 GUID 대신 사용할 수 있는 텍스트 문자열입니다. ProgID 이름은 *Projectname.Coclassname* 형식을 사용합니다.

- **Version**

   공급자의 버전 번호입니다. 기본값은 1입니다.

- **DataSource 클래스**

   C *Shortname* Source 형식의 데이터 소스 클래스 이름입니다.

- **DataSource .h 파일**

   데이터 소스 클래스의 헤더 파일입니다. 이 파일의 이름을 편집하거나 기존 헤더 파일을 선택할 수 있습니다.

- **세션 클래스**

   C *Shortname* Session 형식의 세션 클래스 이름입니다.

- **세션 .h 파일**

   세션 클래스의 헤더 파일입니다. 이 파일의 이름을 편집하거나 기존 헤더 파일을 선택할 수 있습니다.

- **명령 클래스**

   C *Shortname* Command 형식의 명령 클래스 이름입니다.

- **명령 .h 파일**

   명령 클래스의 헤더 파일입니다. 이 이름은 편집할 수 없으며, 행 집합 헤더 파일의 이름에 따라 결정됩니다.

- **행 집합 클래스**

   C *Shortname* Rowset 형식의 행 집합 클래스 이름입니다.

- **행 집합 .h 파일**

   행 집합 클래스의 헤더 파일입니다. 이 파일의 이름을 편집하거나 기존 헤더 파일을 선택할 수 있습니다.

- **행 집합 .cpp 파일**

   공급자의 구현 파일입니다. 이 파일의 이름을 편집하거나 기존 구현 파일을 선택할 수 있습니다.

::: moniker-end

## <a name="see-also"></a>참고 항목

[ATL OLE DB 공급자](../../atl/reference/adding-an-atl-ole-db-provider.md)
