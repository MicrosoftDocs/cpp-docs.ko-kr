---
title: 단순한 읽기 전용 공급자 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2662a071f443967b921c4a8db27713bc7c3e8bb4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096940"
---
# <a name="creating-a-simple-read-only-provider"></a>단순한 읽기 전용 공급자 만들기
ATL 프로젝트 마법사 및 ATL OLE DB 공급자 마법사를 사용 하 여 OLE DB 공급자를 만든 경우에 지원 하 고 다른 기능을 추가할 수 있습니다. 공급자와 그 조건을 소비자에 게 보낼 데이터의 종류를 검사 하 여 디자인을 시작 합니다. 특히 명령, 트랜잭션 및 기타 옵션 개체를 지원 해야 하는지 여부를 결정 하는 것이 유용 합니다. 좋은 설계를 구현 하 고 테스트 신속 하 게 합니다.  
  
 이 예제에서는 두 부분으로 표시 됩니다.  
  
-   첫 번째 부분에 표시 된 하는 방법을 [단순한 읽기 전용 공급자](../../data/oledb/implementing-the-simple-read-only-provider.md) 문자열의 쌍을 읽는 합니다.  
  
-   두 번째 부분에 표시 된 하는 방법을 [단순한 읽기 전용 공급자 향상](../../data/oledb/enhancing-the-simple-read-only-provider.md) 추가 하 여는 `IRowsetLocate` 인터페이스입니다.  
  
## <a name="see-also"></a>참고 항목  
 [OLE DB 공급자 만들기](../../data/oledb/creating-an-ole-db-provider.md)