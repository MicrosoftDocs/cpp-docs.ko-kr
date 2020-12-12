---
description: CNoAccessor 클래스에 대해 자세히 알아보세요.
title: CNoAccessor 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL::CNoAccessor
- CNoAccessor
- ATL.CNoAccessor
helpviewer_keywords:
- CNoAccessor class
ms.assetid: eb669ae5-0a56-49a3-9646-c4ae6239da31
ms.openlocfilehash: 624c72c841280ec56bacf0edd29efeb4b1005988
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170388"
---
# <a name="cnoaccessor-class"></a>CNoAccessor 클래스

는 `TAccessor` `CCommand` `CTable` 접근자 클래스 인수를 필요로 하는 및 등의 템플릿 클래스에 대 한 템플릿 인수 ()로 사용할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
class CNoAccessor
```

## <a name="remarks"></a>설명

`CNoAccessor`클래스가 매개 변수 또는 출력 열을 지원 하지 않도록 하려면를 템플릿 인수로 사용 합니다.

`CNoAccessor` 는 다른 접근자 클래스 메서드에 해당 하는 다음과 같은 스텁 메서드를 구현 합니다.

- `BindColumns` -접근자에 열을 바인딩합니다.

- `BindParameters` -생성 된 매개 변수를 열에 바인딩합니다.

- `Bind` -바인딩을 만듭니다.

- `Close` -접근자를 닫습니다.

- `ReleaseAccessors` -클래스에서 만든 접근자를 해제 합니다.

- `FreeRecordMemory` -해제 해야 하는 현재 레코드의 모든 열을 해제 합니다.

- `GetColumnInfo` -열린 행 집합에서 열 정보를 가져옵니다.

- `GetNumAccessors` -클래스에서 만든 접근자 수를 검색 합니다.

- `IsAutoAccessor` -이동 작업 중 접근자에 대해 데이터가 자동으로 검색 되는 경우 true를 반환 합니다.

- `GetHAccessor` -지정 된 접근자의 접근자 핸들을 검색 합니다.

- `GetBuffer` -책갈피 버퍼에 대 한 포인터를 검색 합니다.

- `NoBindOnNullRowset` -빈 행 집합에 대 한 데이터 바인딩을 방지 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldbcli.h

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)
