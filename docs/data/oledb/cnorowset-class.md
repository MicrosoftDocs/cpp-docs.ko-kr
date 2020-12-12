---
description: '자세히 알아보기: CNoRowset 클래스'
title: CNoRowset 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL.CNoRowset
- ATL::CNoRowset<TAccessor>
- CNoRowset
- ATL.CNoRowset<TAccessor>
- ATL::CNoRowset
helpviewer_keywords:
- CNoRowset class
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
ms.openlocfilehash: 4cdb4631b63ec1f013183713900ffd9574d90fc3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307563"
---
# <a name="cnorowset-class"></a>CNoRowset 클래스

`TRowset` [CCommand](../../data/oledb/ccommand-class.md) 또는 [CTable](../../data/oledb/ctable-class.md)의 템플릿 인수 ()로 사용할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
template <class TAccessor = CAccessorBase>
class CNoRowset
```

### <a name="parameters"></a>매개 변수

*TAccessor*<br/>
접근자 클래스입니다. 기본값은 `CAccessorBase`입니다.

## <a name="remarks"></a>설명

`CNoRowset`명령이 행 집합을 반환 하지 않는 경우 템플릿 인수로 사용 합니다.

`CNoRowset` 는 다른 접근자 클래스 메서드에 해당 하는 다음과 같은 스텁 메서드를 구현 합니다.

- `BindFinished` -바인딩이 완료 된 경우 (를 반환 `S_OK` )를 나타냅니다.

- `Close` -행과 현재 IRowset 인터페이스를 해제 합니다.

- `GetIID` -연결 지점의 인터페이스 ID를 검색 합니다.

- `GetInterface` -인터페이스를 검색 합니다.

- `GetInterfacePtr` -캡슐화 된 인터페이스 포인터를 검색 합니다.

- `SetAccessor` -접근자에 대 한 포인터를 설정 합니다.

- `SetupOptionalRowsetInterfaces` -행 집합에 대 한 선택적 인터페이스를 설정 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldbcli.h

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)
