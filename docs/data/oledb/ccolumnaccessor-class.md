---
description: '자세히 알아보기: CColumnAccessor 클래스'
title: CColumnAccessor 클래스
ms.date: 11/04/2016
f1_keywords:
- CColumnAccessor
- ATL::CColumnAccessor
- ATL.CColumnAccessor
helpviewer_keywords:
- CColumnAccessor class
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
ms.openlocfilehash: 7551f39d34bb4f13b4ffae358db05aede2adb9e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335519"
---
# <a name="ccolumnaccessor-class"></a>CColumnAccessor 클래스

삽입 된 소비자 코드를 생성 합니다.

## <a name="syntax"></a>구문

```cpp
class CColumnAccessor : public CAccessorBase
```

## <a name="remarks"></a>설명

삽입 된 코드에서 모든 열은 별도의 접근자로 바인딩됩니다. 이 클래스는 삽입 된 코드 (예: 디버그할 때 발생할 수 있음)에서 사용 되지만 일반적으로이 클래스 또는 해당 메서드를 직접 사용할 필요는 없습니다.

`CColumnAccessor` 는 다른 접근자 클래스 메서드의 기능에 해당 하는 다음과 같은 스텁 메서드를 구현 합니다.

- `CColumnAccessor` 생성자 개체를 인스턴스화하고 초기화 `CColumnAccessor` 합니다.

- `CreateAccessor` 열 바인딩 구조에 메모리를 할당 하 고 열 데이터 멤버를 초기화 합니다.

- `BindColumns` 열을 접근자에 바인딩합니다.

- `SetParameterBuffer` 매개 변수에 대 한 버퍼를 할당 합니다.

- `AddParameter` 매개 변수 엔트리를 매개 변수 항목 구조에 추가 합니다.

- `HasOutputColumns` 접근자에 출력 열이 있는지 여부를 확인 합니다.

- `HasParameters` 접근자에 매개 변수가 있는지 여부를 확인 합니다.

- `BindParameters` 만든 매개 변수를 열에 바인딩합니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldbcli.h

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)
