---
title: 마법사를 사용하지 않고 소비자 만들기
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
ms.openlocfilehash: 85e95afa92c8a968865d9a3031e1a309e68ae7d3
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/20/2019
ms.locfileid: "79544701"
---
# <a name="creating-a-consumer-without-using-a-wizard"></a>마법사를 사용하지 않고 소비자 만들기

다음 예제에서는 기존 ATL 프로젝트에 OLE DB 소비자 지원을 추가한다고 가정합니다. MFC 애플리케이션에 OLE DB 소비자 지원을 추가하려는 경우 **MFC 애플리케이션 마법사**를 실행해야 합니다. 이 마법사는 필요한 모든 지원을 만들고, 애플리케이션을 실행하는 데 필요한 MFC 루틴을 호출합니다.

**ATL OLE DB 소비자 마법사**를 사용하지 않고 OLE DB 소비자 지원을 추가하려면 다음을 수행합니다.

- *.Pch .h* 파일에서 다음 `#include` 문을 추가 합니다.

    ```cpp
    #include <atlbase.h>
    #include <atldbcli.h>
    #include <atldbsch.h> // if you are using schema templates
    ```

소비자는 일반적으로 다음과 같은 일련의 작업을 프로그래밍 방식으로 수행합니다.

1. 지역 변수에 열을 바인딩하는 사용자 레코드 클래스를 만듭니다. 이 예제에서 `CMyTableNameAccessor`는 사용자 레코드 클래스입니다([사용자 레코드](../../data/oledb/user-records.md) 참조). 이 클래스에는 열 맵과 매개 변수 맵이 포함됩니다. 열 맵에서 지정한 각 필드에 대한 데이터 멤버를 사용자 레코드 클래스에 선언합니다. 이러한 각 데이터 멤버에 대해 상태 데이터 멤버와 길이 데이터 멤버도 선언합니다. 자세한 내용은 [마법사 생성 접근자의 필드 상태 데이터 멤버](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md)를 참조하세요.

    > [!NOTE]
    > 고유한 소비자를 작성하는 경우 데이터 변수가 상태 및 길이 변수 앞에 와야 합니다.

- 데이터 소스 및 세션을 인스턴스화합니다. 사용할 접근자 및 행 집합의 형식을 결정하고, [CCommand](../../data/oledb/ccommand-class.md) 또는 [CTable](../../data/oledb/ctable-class.md)을 사용하여 행 집합을 인스턴스화합니다.

    ```cpp
    CDataSource ds;
    CSession ss;
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor>>
    ```

- `CoInitialize`를 호출하여 COM을 초기화합니다. 주 코드에서 호출됩니다. 예를 들면 다음과 같습니다.

    ```cpp
    HRESULT hr = CoInitialize(NULL);
    ```

- [CDataSource::Open](../../data/oledb/cdatasource-open.md) 또는 해당 변형 중 하나를 호출합니다.

- 데이터 소스에 대한 연결과 세션을 열고, 행 집합을 열어서 초기화합니다(명령이 있을 경우 명령도 실행함).

    ```cpp
    hr = ds.Open();
    hr = ss.Open(ds);
    hr = rs.Open();            // (Open also executes the command)
    ```

- 필요에 따라 `CDBPropSet::AddProperty`를 사용하여 행 집합 속성을 설정하고 `rs.Open`에 매개 변수로 전달합니다. 이 작업을 수행하는 방법의 예제는 `GetRowsetProperties`소비자 마법사 생성 메서드[의 ](../../data/oledb/consumer-wizard-generated-methods.md)를 참조하세요.

- 이제 행 집합을 사용하여 데이터를 검색/조작할 수 있습니다.

- 애플리케이션이 완료되면 연결, 세션 및 행 집합을 닫습니다.

    ```cpp
    rs.Close();
    ss.Close();
    ds.Close();
    ```

   명령을 사용하는 경우 `ReleaseCommand` 다음에 `Close`를 호출하는 것이 좋습니다. [CCommand::Close](../../data/oledb/ccommand-close.md)의 코드 예제에서는 `Close` 및 `ReleaseCommand`를 호출하는 방법을 보여 줍니다.

- `CoUnInitialize`를 호출하여 COM 초기화를 취소합니다. 주 코드에서 호출됩니다.

    ```cpp
    CoUninitialize();
    ```

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 만들기](../../data/oledb/creating-an-ole-db-consumer.md)