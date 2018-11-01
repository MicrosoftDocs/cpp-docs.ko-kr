---
title: 책갈피 사용
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- OLE DB providers, bookmark support
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
ms.openlocfilehash: 1f8ef4c25ad921dad66e5587f4005585b3e017f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635658"
---
# <a name="using-bookmarks"></a>책갈피 사용

행 집합을 열기 전에 알려야 공급자 책갈피를 사용 하려고 합니다. 이 위해 설정 된 `DBPROP_BOOKMARKS` 속성을 **true** 속성을 설정 합니다. 공급자 특수 BOOKMARK_ENTRY 매크로 사용 해야 하므로 열 0으로 책갈피를 검색 및 `CBookmark` 정적 접근자를 사용 하는 경우 클래스입니다. `CBookmark` 책갈피 버퍼의 길이 (바이트)를 인수가 있는 템플릿 클래스가입니다. 책갈피에 필요한 버퍼의 길이 공급자에 따라 달라 집니다. 다음 예제에서와 같이 ODBC OLE DB 공급자를 사용 하는 경우 버퍼에는 4 바이트 여야 합니다.

```cpp
class CProducts
{
public:
   CBookmark<4> bookmark;

   BEGIN_COLUMN_MAP(CProducts)
      BOOKMARK_ENTRY(bookmark)
   END_COLUMN_MAP()
};
```

그런 다음 다음 코드에 의해 사용:

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_BOOKMARKS, true);

CTable<CAccessor<CProducts>> product;
CSession session;
product.Open(session, "Products", &propset);
```

사용 하는 경우 `CDynamicAccessor`, 버퍼 런타임에 동적으로 설정 합니다. 특수 버전을 사용할 수 있습니다이 경우 `CBookmark` 버퍼 길이 지정 하지 않습니다. 함수를 사용 하 여 `GetBookmark` 이 코드 샘플에 표시 된 대로 현재 레코드에서 책갈피를 검색 하려면:

```cpp
CTable<CDynamicAccessor> product;
CBookmark<> bookmark;
CDBPropSet propset(DBPROPSET_ROWSET);
CSession session;

propset.AddProperty(DBPROP_BOOKMARKS, true);
product.Open(session, "Products", &propset);
product.MoveNext();
product.GetBookmark(&bookmark);
```

공급자의 책갈피 지원에 대 한 자세한 내용은 [공급자의 책갈피 지원](../../data/oledb/provider-support-for-bookmarks.md)합니다.

## <a name="see-also"></a>참고 항목

[접근자 사용](../../data/oledb/using-accessors.md)