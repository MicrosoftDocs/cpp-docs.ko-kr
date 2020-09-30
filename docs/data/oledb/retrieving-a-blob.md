---
title: BLOB 검색
ms.date: 10/24/2018
helpviewer_keywords:
- retrieving BLOBs
- BLOB (binary large object), retrieving
- OLE DB, BLOBs (binary large objects)
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
ms.openlocfilehash: 352841595e8b197407ccb52a22c8b0502d314c98
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509504"
---
# <a name="retrieving-a-blob"></a>BLOB 검색

다양 한 방법으로 BLOB (binary large object)를 검색할 수 있습니다. `DBTYPE_BYTES`를 사용 하 여 BLOB를 바이트 시퀀스로 검색 하거나와 같은 인터페이스를 사용할 수 있습니다 `ISequentialStream` . 자세한 내용은 **OLE DB 프로그래머 참조**의 [Blob 및 OLE 개체](/previous-versions/windows/desktop/ms711511(v=vs.85)) 를 참조 하세요.

다음 코드에서는를 사용 하 여 BLOB을 검색 하는 방법을 보여 줍니다 `ISequentialStream` . [BLOB_ENTRY](./macros-and-global-functions-for-ole-db-consumer-templates.md#blob_entry) 매크로를 사용 하 여 인터페이스와 인터페이스에 사용 되는 플래그를 지정할 수 있습니다. 테이블을 연 후 코드는를 `Read` 반복 해 서 호출 `ISequentialStream` 하 여 BLOB에서 바이트를 읽습니다. `Release`다음 레코드를 가져오기 위해를 호출 하기 전에 코드에서 인터페이스 포인터를 삭제 하기 위해를 호출 합니다 `MoveNext` .

```cpp
class CCategories
{
public:
   ISequentialStream* pPicture;

BEGIN_COLUMN_MAP(CCategories)
   BLOB_ENTRY(4, IID_ISequentialStream, STGM_READ, pPicture)
END_COLUMN_MAP()
};
```

그런 다음, 다음 코드에서 사용 됩니다.

```cpp
CTable<CAccessor<CCategories>> categories;
ULONG cb;
BYTE myBuffer[65536];

categories.Open(session, "Categories");

while (categories.MoveNext() == S_OK)
{
   do
   {
      categories.pPicture->Read(myBuffer, 65536, &cb);
      // Do something with the buffer
   } while (cb > 0);
   categories.pPicture->Release();
}
```

BLOB 데이터를 처리 하는 매크로에 대 한 자세한 내용은 [OLE DB 소비자 템플릿에 대 한 매크로 및 전역 함수](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)의 **열 맵 매크로** 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[접근자 사용](../../data/oledb/using-accessors.md)<br/>
[OLE DB 소비자 템플릿에 대 한 매크로 및 전역 함수](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
