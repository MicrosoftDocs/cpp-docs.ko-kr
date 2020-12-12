---
description: '자세한 정보: 책갈피 사용'
title: 책갈피 사용
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- OLE DB providers, bookmark support
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
ms.openlocfilehash: d0cf27a5f93b3e6b00fa6f8cbb69ae7414f4d819
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319159"
---
# <a name="using-bookmarks"></a>책갈피 사용

행 집합을 열기 전에 책갈피를 사용 하려는 공급자에 게 지시 해야 합니다. 이렇게 하려면 `DBPROP_BOOKMARKS` 속성 집합에서 속성을로 설정 **`true`** 합니다. 공급자는 책갈피를 열 0으로 검색 하므로 `CBookmark` 정적 접근자를 사용 하는 경우 특수 매크로 BOOKMARK_ENTRY 및 클래스를 사용 해야 합니다. `CBookmark` 는 인수가 책갈피 버퍼의 길이 (바이트) 인 템플릿 클래스입니다. 책갈피에 필요한 버퍼의 길이는 공급자에 따라 달라 집니다. 다음 예제와 같이 ODBC OLE DB 공급자를 사용 하는 경우 버퍼는 4 바이트 여야 합니다.

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

그런 다음, 다음 코드에서 사용 됩니다.

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_BOOKMARKS, true);

CTable<CAccessor<CProducts>> product;
CSession session;
product.Open(session, "Products", &propset);
```

를 사용 하는 경우 `CDynamicAccessor` 버퍼는 런타임에 동적으로 설정 됩니다. 이 경우 버퍼 길이를 지정 하지 않는의 특수 버전을 사용할 수 있습니다 `CBookmark` . 다음 코드 샘플과 같이 함수를 사용 `GetBookmark` 하 여 현재 레코드에서 책갈피를 검색 합니다.

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

공급자에서 책갈피를 지 원하는 방법에 대 한 자세한 내용은 [공급자의 책갈피 지원](../../data/oledb/provider-support-for-bookmarks.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[접근자 사용](../../data/oledb/using-accessors.md)
