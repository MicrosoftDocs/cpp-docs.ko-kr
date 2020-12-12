---
description: '자세한 정보: 사용자 레코드'
title: 사용자 레코드
ms.date: 05/09/2019
helpviewer_keywords:
- records, user
- OLE DB providers, user record
- user records
- user records, described
- rowsets, user record
ms.assetid: 9c0d2864-2738-4f62-a750-1016d9c3523f
ms.openlocfilehash: f858660800391eff45cb88115f8fb09afa26a77f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272502"
---
# <a name="user-record"></a>사용자 레코드

> [!NOTE]
> Visual Studio 2019 이상에서는 ATL OLE DB 공급자 마법사를 사용할 수 없습니다.

사용자 레코드는 행 집합의 열 데이터를 나타내는 코드 및 데이터 구조를 제공합니다. 컴파일 시간이나 런타임에 사용자 레코드를 만들 수 있습니다. **ATL OLE DB 공급자 마법사** 를 사용하여 공급자를 만드는 경우, 마법사에서 다음과 같은 기본 사용자 레코드를 만듭니다(공급자 이름(짧은 이름)으로 *MyProvider* 를 지정했다고 가정).

```cpp
class CWindowsFile:
   public WIN32_FIND_DATA
{
public:
  
BEGIN_PROVIDER_COLUMN_MAP(CMyProviderWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)
END_PROVIDER_COLUMN_MAP()
  
};
```

OLE DB 공급자 템플릿은 클라이언트와의 상호 작용에 대한 모든 OLE DB 세부 정보를 처리합니다. 응답에 필요한 열 데이터를 얻기 위해 공급자는 `GetColumnInfo` 함수를 호출합니다. 이 함수를 사용자 레코드에 배치해야 합니다. 예를 들어 .h 파일에서 다음과 같이 선언하면 사용자 레코드에서 `GetColumnInfo`를 명시적으로 재정의할 수 있습니다.

```cpp
template <class T>
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols)
```

이 코드는 다음과 같습니다.

```cpp
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)
```

그런 다음, 사용자 레코드의 .cpp 파일에서 `GetColumnInfo`를 구현합니다.

PROVIDER_COLUMN_MAP 매크로는 `GetColumnInfo` 함수를 만드는 데 도움이 됩니다.

- BEGIN_PROVIDER_COLUMN_MAP은 함수 프로토타입 및 `ATLCOLUMNINFO` 구조체의 정적 배열을 정의합니다.

- PROVIDER_COLUMN_ENTRY는 단일 `ATLCOLUMNINFO`를 정의하고 초기화합니다.

- END_PROVIDER_COLUMN_MAP은 배열과 함수를 닫습니다. 또한 *pcCols* 매개 변수에 배열 요소 수를 배치합니다.

런타임에 사용자 레코드가 생성되면 `GetColumnInfo`는 *pThis* 매개 변수를 사용하여 행 집합 또는 명령 인스턴스에 대한 포인터를 받습니다. 이 포인터에서 열 정보를 가져올 수 있도록 명령과 행 집합이 `IColumnsInfo` 인터페이스를 지원해야 합니다.

사용자 레코드를 사용하는 명령과 행 집합은 `CommandClass` 및 `RowsetClass`입니다.

사용자 레코드에서 `GetColumnInfo`를 재정의하는 방법의 자세한 예제는 [소비자에게 반환되는 열을 동적으로 결정](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
