---
title: 단순한 읽기 전용 공급자 만들기
ms.date: 10/26/2018
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
ms.openlocfilehash: 2ac8e45ca06a5566923141adf5a22dc6710eeeab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432606"
---
# <a name="creating-a-simple-read-only-provider"></a>단순한 읽기 전용 공급자 만들기

**ATL 프로젝트 마법사**와 **ATL OLE DB 공급자 마법사**를 사용하여 OLE DB 공급자를 만들었으면 지원할 다른 기능을 추가할 수 있습니다. 먼저 소비자에게 보낼 데이터 종류와 데이터를 보내는 조건을 검토하여 공급자 디자인을 시작합니다. 특히 명령이나 트랜잭션 및 기타 선택적 개체를 지원해야 하는지를 결정하는 것이 중요합니다. 시작할 때 디자인을 잘 하면 구현과 테스트 속도가 빨라집니다.

다음 두 장에서 예제가 제공됩니다.

- 첫 번째 장에서는 문자열 쌍을 읽는 [단순한 읽기 전용 공급자 구현](../../data/oledb/implementing-the-simple-read-only-provider.md) 방법을 볼 수 있습니다.

- 두 번째 장에서는 `IRowsetLocate` 인터페이스를 추가하여 [단순한 읽기 전용 공급자의 기능 향상](../../data/oledb/enhancing-the-simple-read-only-provider.md) 방법을 볼 수 있습니다.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 만들기](../../data/oledb/creating-an-ole-db-provider.md)<br/>
