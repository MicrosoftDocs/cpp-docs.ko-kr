---
title: 단순 소비자 만들기
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
ms.openlocfilehash: 0b142a73f66a796f3e22bae0aeacb88dc018aea9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501865"
---
# <a name="creating-a-simple-consumer"></a>단순 소비자 만들기

::: moniker range="vs-2019"

Visual Studio 2019 이상에서는 ATL OLE DB 소비자 마법사를 사용할 수 없습니다. 수동으로 기능을 추가할 수는 있습니다. 자세한 내용은 [마법사를 사용하지 않고 소비자 만들기](creating-a-consumer-without-using-a-wizard.md)를 참조하세요.

::: moniker-end

::: moniker range="<=vs-2017"

**ATL 프로젝트 마법사** 및 **ATL OLE DB 소비자 마법사**를 사용하여 OLE DB 템플릿 소비자를 생성합니다.

## <a name="to-create-a-console-application-for-an-ole-db-consumer"></a>OLE DB 소비자의 콘솔 애플리케이션을 만들려면 다음을 수행합니다.

1. **파일** 메뉴에서 **새로 만들기**를 클릭한 다음 **프로젝트**를 클릭합니다.

   **새 프로젝트** 대화 상자가 나타납니다.

1. **프로젝트 형식** 창에서 **설치됨** > **Visual C++** > **Windows 데스크톱** 폴더를 클릭한 다음, **템플릿** 창에서 **Windows 데스크톱 마법사** 아이콘을 클릭합니다. **이름** 상자에 프로젝트 이름을 입력합니다(예: *MyCons*).

1. **확인**을 클릭합니다.

   **Windows 데스크톱 프로젝트** 마법사가 나타납니다.

1. **애플리케이션 설정** 페이지에서 **콘솔 애플리케이션**을 선택한 다음, **ATL에 대한 공용 헤더 파일 추가**를 선택합니다.

1. **확인**을 클릭하여 마법사를 닫고 프로젝트를 생성합니다.

다음으로, **ATL OLE DB 소비자 마법사**를 사용하여 OLE DB 소비자 개체를 추가합니다.

## <a name="to-create-a-consumer-with-the-atl-ole-db-consumer-wizard"></a>ATL OLE DB 소비자 마법사를 사용하여 소비자를 만들려면 다음을 수행합니다.

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭 `MyCons` 합니다.

1. 바로 가기 메뉴에서 **추가**를 클릭한 다음, **새 항목**을 클릭합니다.

   **새 항목 추가** 대화 상자가 나타납니다.

1. **범주** 창에서 **설치됨** > **Visual C++** > **ATL**을 클릭하고 **템플릿** 창에서 **ATL OLEDB 소비자** 아이콘을 클릭한 다음, **추가**를 클릭합니다.

   **ATL OLEDB 소비자 마법사**가 나타납니다.

1. **데이터 소스** 단추를 클릭합니다.

   **데이터 연결 속성** 대화 상자가 나타납니다.

1. **데이터 연결 속성** 대화 상자에서 다음을 수행합니다.

   1. **공급자** 탭에서 OLE DB 공급자를 지정합니다.

   1. **연결** 탭에서 서버 이름, 로그온 ID, 서버의 데이터 소스 및 데이터베이스에 대한 암호 등 필요한 정보를 지정합니다.

      > [!NOTE]
      > **데이터 연결 속성** 대화 상자의 **암호 저장 허용** 기능을 사용하면 보안 문제가 발생합니다. **서버에 로그온 하기 위한 정보 입력**에는 **Windows NT 통합 보안을 사용** 하 고 **특정 사용자 이름 및 암호를 사용**하는 두 가지 라디오 단추가 있습니다.

      > [!NOTE]
      > **특정 사용자 이름 및 암호 사용**을 선택하면 암호를 저장할 수 있지만(**암호 저장 허용** 확인란 사용), 이 옵션은 안전하지 않습니다. **Windows NT 통합 보안 사용**을 선택하는 것이 좋습니다. 이 옵션은 Windows NT를 사용하여 ID를 검증합니다.

      > [!NOTE]
      > Windows NT 통합 보안을 사용할 수 없는 경우, 중간 계층 애플리케이션을 사용하여 사용자에게 암호를 묻는 메시지를 표시하거나 소스 코드 대신 보안 메커니즘이 있는 위치에 암호를 저장하여 보호해야 합니다.

   1. 공급자와 기타 설정을 선택한 후 **연결 테스트**를 클릭하여 이전 대화 상자 페이지에서 선택한 내용을 검증합니다. **결과** 상자에 `Test connection succeeded`가 보고되면 **확인**을 클릭하여 데이터 연결을 만듭니다.

   **데이터베이스 개체 선택** 대화 상자가 나타납니다.

1. 트리 컨트롤을 사용하여 테이블, 뷰 또는 저장 프로시저를 선택합니다. 이 예제에서는 `Northwind` 데이터베이스의 `Products` 테이블을 선택합니다.

1. **확인**을 클릭합니다. 이렇게 하면 **ATL OLE DB 소비자 마법사**로 돌아갑니다.

1. 선택한 테이블, 뷰 또는 저장 프로시저의 이름에 따라 `Class` 및 **.h 파일**의 이름이 완성됩니다. 필요한 경우 이 이름을 편집할 수 있습니다.

1. 마법사에서 기본값인 [OLE DB 소비자 특성](../../windows/attributes/ole-db-consumer-attributes.md) 대신 [OLE DB 템플릿 클래스](../../data/oledb/ole-db-consumer-templates-reference.md)를 사용하여 소비자 코드를 만들려면 **특성 사용** 확인란의 선택을 취소합니다.

1. **형식**에서 **명령**을 선택합니다.

   **명령**을 선택하면 [CCommand](../../data/oledb/ccommand-class.md) 기반 소비자가 생성되고, **테이블**을 선택하면 [CTable](../../data/oledb/ctable-class.md) 기반 소비자가 생성됩니다. 선택한 개체에 따라 테이블 또는 명령 클래스의 이름이 지정되지만, 이름을 편집할 수 있습니다.

1. **지원**에서 **변경**, **삽입** 및 **삭제** 확인란을 선택 취소된 상태로 둡니다.

   행 집합의 레코드 변경, 삽입 및 삭제를 지원하려면 **변경**, **삽입** 및 **삭제** 확인란을 선택합니다. 데이터 저장소에 데이터를 쓰는 방법에 대한 자세한 내용은 [행 집합 업데이트](../../data/oledb/updating-rowsets.md)를 참조하세요.

1. **마침**을 클릭하여 소비자를 만듭니다.

[소비자 마법사 생성 클래스](../../data/oledb/consumer-wizard-generated-classes.md)에 표시된 대로, 명령 클래스와 사용자 레코드 클래스가 생성됩니다. 명령 클래스에는 마법사의 `Class` 상자에 입력한 이름이 지정되고(이 예제에서는 `CProducts`), 사용자 레코드 클래스에는 “*ClassName*Accessor” 형식의 이름이 지정됩니다(이 예제에서는 `CProductsAccessor`).

> [!NOTE]
> `Products.h`에 다음 줄이 배치됩니다.

```cpp
#error Security Issue: The connection string may contain a password
```

> [!NOTE]
> 이 줄을 사용하면 소비자 애플리케이션이 컴파일되지 않고, 연결 문자열에서 하드 코드된 암호를 확인하라는 알림이 표시됩니다. 연결 문자열을 확인한 후 이 코드 줄을 제거해도 됩니다.

::: moniker-end

## <a name="see-also"></a>참고 항목

[마법사를 사용 하 여 OLE DB 소비자 만들기](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
