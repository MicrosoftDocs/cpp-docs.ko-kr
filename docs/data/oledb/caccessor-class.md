---
title: CAccessor 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL.CAccessor<T>
- ATL::CAccessor
- CAccessor
- ATL::CAccessor<T>
- ATL.CAccessor
helpviewer_keywords:
- CAccessor class
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
ms.openlocfilehash: 032274d7dc85aa823cd28cf61e4606903f13ad9e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509558"
---
# <a name="caccessor-class"></a>CAccessor 클래스

접근자 형식 중 하나를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
class CAccessor : public CAccessorBase, public T
```

### <a name="parameters"></a>매개 변수

*T*<br/>
사용자 레코드 클래스입니다.

## <a name="remarks"></a>설명

레코드가 데이터 원본에 정적으로 바인딩될 때 사용 됩니다. 레코드는 버퍼를 포함 합니다. 이 클래스는 행 집합에서 여러 접근자를 지원 합니다.

데이터베이스의 구조와 유형을 알고 있는 경우이 접근자 유형을 사용 합니다.

접근자에 해제 해야 하는 메모리 (예: 또는 인터페이스)를 가리키는 필드가 포함 된 경우 `BSTR` 다음 레코드를 읽기 전에 멤버 함수 [CAccessorRowset:: FreeRecordMemory](./caccessorrowset-class.md#freerecordmemory) 를 호출 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldbcli.h

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)
