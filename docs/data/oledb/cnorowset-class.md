---
title: CNoRowset 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CNoRowset
- ATL::CNoRowset<TAccessor>
- CNoRowset
- ATL.CNoRowset<TAccessor>
- ATL::CNoRowset
dev_langs:
- C++
helpviewer_keywords:
- CNoRowset class
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f14ad79e1cbd2207b4eb1582cb80e0107d68ec39
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064240"
---
# <a name="cnorowset-class"></a>CNoRowset 클래스

템플릿 인수로 사용할 수 있습니다 (`TRowset`)에 대 한 [CCommand](../../data/oledb/ccommand-class.md) 하거나 [CTable](../../data/oledb/ctable-class.md)합니다.

## <a name="syntax"></a>구문

```cpp
template <class TAccessor = CAccessorBase>
class CNoRowset
```

### <a name="parameters"></a>매개 변수

*TAccessor*<br/>
접근자 클래스입니다. 기본값은 `CAccessorBase`입니다.

## <a name="remarks"></a>설명

사용 하 여 `CNoRowset` 명령 행 집합을 반환 하지 않는 경우 템플릿 인수로 합니다.

`CNoRowset` 각 메서드에 해당 하는 다른 접근자 클래스 다음 스텁 메서드를 구현 합니다.

- `BindFinished` -바인딩이 완료 되었을 때 나타냅니다 (반환 `S_OK`).

- `Close` -행 및 현재 IRowset 인터페이스를 해제합니다.

- `GetIID` -연결 지점의 인터페이스 ID를 검색 합니다.

- `GetInterface` -인터페이스를 검색 합니다.

- `GetInterfacePtr` -캡슐화 된 인터페이스 포인터를 검색합니다.

- `SetAccessor` -접근자에 대 한 포인터를 설정합니다.

- `SetupOptionalRowsetInterfaces` -행 집합에 대 한 선택적 인터페이스를 설정합니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldbcli.h

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)