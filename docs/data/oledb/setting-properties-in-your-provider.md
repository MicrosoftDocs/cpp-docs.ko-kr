---
title: 공급자에 속성 설정
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB providers, properties
- properties [C++], OLE DB provider
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
ms.openlocfilehash: 3717282d284990b1b8038f6954ee971938cf7921
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509477"
---
# <a name="setting-properties-in-your-provider"></a>공급자에 속성 설정

원하는 속성에 대 한 속성 그룹 및 속성 ID를 찾습니다. 자세한 내용은 **OLE DB 프로그래머 참조**의 [OLE DB 속성](/previous-versions/windows/desktop/ms722734(v=vs.85)) 을 참조 하세요.

마법사에서 생성 된 공급자 코드에서 속성 그룹에 해당 하는 속성 맵을 찾습니다. 속성 그룹의 이름은 일반적으로 개체의 이름에 해당 합니다. 명령 및 행 집합 속성은 명령 또는 행 집합에서 찾을 수 있습니다. 데이터 원본 개체에서 데이터 원본 및 초기화 속성을 찾을 수 있습니다.

속성 맵에서 [PROPERTY_INFO_ENTRY_EX](./macros-for-ole-db-provider-templates.md#property_info_entry_ex) 매크로를 추가 합니다. PROPERTY_INFO_ENTRY_EX는 네 개의 매개 변수를 사용 합니다.

- 속성에 해당 하는 속성 ID입니다. 속성 이름 앞에서 처음 7 개 문자 ("DBPROP_")를 제거 합니다. 예를 들어를 추가 하려는 경우 `DBPROP_MAXROWS` 을 `MAXROWS` 첫 번째 요소로 전달 합니다. 사용자 지정 속성인 경우 전체 GUID 이름 (예:)을 전달 `DBMYPROP_MYPROPERTY` 합니다.

- **OLE DB 프로그래머 참조**의 속성 [OLE DB](/previous-versions/windows/desktop/ms722734(v=vs.85)) 속성의 variant 형식입니다. 데이터 형식에 해당 하는 VT_ 유형 (예: VT_BOOL 또는 VT_I2)을 입력 합니다.

- 속성을 읽을 수 있고 쓸 수 있는지 여부와 속성이 속한 그룹을 나타내는 플래그입니다. 예를 들어 다음 코드는 행 집합 그룹에 속하는 읽기/쓰기 속성을 나타냅니다.

    ```cpp
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE
    ```

- 속성의 기준 값입니다. 예를 들어 `VARIANT_FALSE` 정수 형식의 경우 부울 형식 또는 0 일 수 있습니다. 속성은 변경 되지 않는 한이 값을 갖습니다.

    > [!NOTE]
    > 일부 속성은 책갈피 또는 업데이트와 같은 다른 속성에 연결 되거나 연결 됩니다. 소비자가 하나의 속성을 true로 설정 하면 다른 속성도 설정 될 수도 있습니다. OLE DB 공급자 템플릿에서는 [가공선 Lprops:: OnPropertyChanged](./cutlprops-class.md#onpropertychanged)메서드를 통해이를 지원 합니다.

## <a name="properties-ignored-by-microsoft-ole-db-providers"></a>Microsoft OLE DB 공급자가 무시 하는 속성

Microsoft OLE DB 공급자는 다음과 같은 OLE DB 속성을 무시 합니다.

- `DBPROP_MAXROWS` 는 읽기 전용 공급자에 대해서만 작동 합니다. 여기서 `DBPROP_IRowsetChange` 및 `DBPROP_IRowsetUpdate` 는입니다 **`false`** . 그렇지 않으면이 속성이 지원 되지 않습니다.

- `DBPROP_MAXPENDINGROWS` 무시 됩니다. 공급자는 자체 제한을 지정 합니다.

- `DBPROP_MAXOPENROWS` 무시 됩니다. 공급자는 자체 제한을 지정 합니다.

- `DBPROP_CANHOLDROWS` 무시 됩니다. 공급자는 자체 제한을 지정 합니다.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿 사용](../../data/oledb/working-with-ole-db-provider-templates.md)
