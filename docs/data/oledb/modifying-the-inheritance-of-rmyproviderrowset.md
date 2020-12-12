---
description: '자세히 알아보기: RCustomRowset의 상속 수정'
title: RCustomRowset의 상속 수정
ms.date: 10/26/2018
helpviewer_keywords:
- RMyProviderRowset
- inheritance [C++]
- RCustomRowset
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
ms.openlocfilehash: c54533122083c526ad12ac6514efa3ad9ba47cf5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287010"
---
# <a name="modifying-the-inheritance-of-rcustomrowset"></a>RCustomRowset의 상속 수정

`IRowsetLocate`단순한 읽기 전용 공급자 예제에 인터페이스를 추가 하려면의 상속을 수정 `CCustomRowset` 합니다. 처음에는 `CCustomRowset` 에서 상속 `CRowsetImpl` 합니다. 에서 상속 하도록 수정 해야 `CRowsetBaseImpl` 합니다.

이렇게 하려면 `CCustomRowsetImpl` *사용자 지정* RS. h에서 새 클래스를 만듭니다.

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

template <class T, class Storage, class CreatorClass, class ArrayType = CAtlArray<Storage>>
class CMyRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, CSimpleRow, IRowsetLocateImpl< T, IRowsetLocate >>
{
...
};
```

이제 다음과 같이 *사용자 지정* RS. h에서 COM 인터페이스 맵을 편집 합니다.

```cpp
BEGIN_COM_MAP(CMyRowsetImpl)
   COM_INTERFACE_ENTRY(IRowsetLocate)
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)
END_COM_MAP()
```

이 코드는 `CMyRowsetImpl` 및 인터페이스를 모두 호출 하도록에 지시 하는 COM 인터페이스 맵을 만듭니다 `QueryInterface` `IRowset` `IRowsetLocate` . 다른 행 집합 클래스에 대 한 모든 구현을 가져오기 위해 맵은 `CMyRowsetImpl` 클래스를 `CRowsetBaseImpl` OLE DB 템플릿에 의해 정의 된 클래스로 다시 연결 합니다. 맵은 COM_INTERFACE_ENTRY_CHAIN 매크로를 사용 하 여 `CRowsetBaseImpl` 호출에 대 한 응답으로 COM 맵을 검색 하도록 OLE DB 템플릿을 지시 합니다 `QueryInterface` .

마지막으로 다음과 `CCustomRowset` `CMyRowsetBaseImpl` `CCustomRowset` 같이를에서 상속 하도록를 수정 하 여에 연결 합니다 `CMyRowsetImpl` .

```cpp
class CCustomRowset : public CMyRowsetImpl<CCustomRowset, CCustomWindowsFile, CCustomCommand>
```

`CCustomRowset` 이제는 `IRowsetLocate` 행 집합 클래스에 대 한 나머지 구현을 활용 하면서 인터페이스를 사용할 수 있습니다.

이 작업이 완료 되 면 [소비자에 게 반환 되는 열을 동적으로 결정할](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md)수 있습니다.

## <a name="see-also"></a>참고 항목

[간단한 Read-Only 공급자 향상](../../data/oledb/enhancing-the-simple-read-only-provider.md)<br/>
