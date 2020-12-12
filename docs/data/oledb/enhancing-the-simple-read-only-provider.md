---
description: '자세한 정보: 간단한 Read-Only 공급자 향상'
title: 단순한 읽기 전용 공급자의 기능 향상
ms.date: 10/26/2018
helpviewer_keywords:
- read-only poviders [C++]
- IRowsetLocate class
- IRowsetLocate class, adding to OLE DB template providers
- simple read-only poviders [C++]
ms.assetid: cba0e09f-44c1-41c1-9456-332aa13dc158
ms.openlocfilehash: 00a0ea4fb9b759447026353ba0d78c7c856b15ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317638"
---
# <a name="enhancing-the-simple-read-only-provider"></a>단순한 읽기 전용 공급자의 기능 향상

이 섹션에서는 이전 섹션에서 만든 [간단한 읽기 전용 공급자](../../data/oledb/implementing-the-simple-read-only-provider.md) 를 개선 하는 방법을 보여 줍니다. `IRowsetLocateImpl` 인터페이스에 대 한 구현을 만들고 `IRowsetLocate` 책갈피 지원을 추가 합니다.

작동 하는 공급자가 있는 경우 공급자를 업데이트 하거나, 트랜잭션을 처리 하거나, 행 인출 알고리즘의 성능을 향상 시키기 위해이 기능을 향상 시킬 수 있습니다. 대부분의 공급자 기능 향상에는 기존 COM 개체에 인터페이스를 추가 하는 작업이 포함 됩니다.

다음 항목의 예제에서는에 인터페이스를 추가 하 여 행 가져오기 메커니즘을 향상 시킵니다 `IRowsetLocate` `CAgentRowset` . 이 항목에서는 다음 작업을 수행 하는 방법을 보여 줍니다.

- [RCustomRowset을 IRowsetLocate에서 상속 하도록 설정](../../data/oledb/modifying-the-inheritance-of-rmyproviderrowset.md)합니다.

- [소비자에 게 반환 되는 열을 동적으로 결정](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)합니다.

## <a name="see-also"></a>참고 항목

[간단한 Read-Only 공급자 만들기](../../data/oledb/creating-a-simple-read-only-provider.md)<br/>
