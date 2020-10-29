---
title: 단순한 읽기 전용 공급자 만들기
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
ms.openlocfilehash: c7c6c5bb2691a110a6368decd875f5a5a06b11b5
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919191"
---
# <a name="creating-a-simple-read-only-provider"></a>단순한 읽기 전용 공급자 만들기

::: moniker range="msvc-160"

Visual Studio 2019 이상에서는 ATL OLE DB 공급자 마법사를 사용할 수 없습니다.

::: moniker-end

::: moniker range="<=msvc-150"

**ATL 프로젝트 마법사** 및 **ATL OLE DB 공급자 마법사** 를 사용하여 OLE DB 공급자를 만든 경우, 지원하려는 다른 기능을 추가할 수 있습니다. 소비자에게 보낼 데이터 종류와 해당 조건을 검사하여 공급자 설계를 시작합니다. 특히 명령, 트랜잭션 및 기타 선택적 개체를 지원해야 하는지 여부를 확인하는 것이 중요합니다. 사전 설계가 완벽하면 구현 및 테스트를 빠르게 진행할 수 있습니다.

이 예제는 다음 두 부분으로 제공됩니다.

- 첫 번째 부분에서는 문자열 쌍을 읽는 [단순한 읽기 전용 공급자를 만드는](../../data/oledb/implementing-the-simple-read-only-provider.md) 방법을 보여 줍니다.

- 두 번째 부분에서는 `IRowsetLocate` 인터페이스를 추가하여 [단순한 읽기 전용 공급자의 기능을 향상](../../data/oledb/enhancing-the-simple-read-only-provider.md)하는 방법을 보여 줍니다.

::: moniker-end

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 만들기](../../data/oledb/creating-an-ole-db-provider.md)<br/>
