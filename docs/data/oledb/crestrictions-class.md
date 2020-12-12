---
description: '자세히 알아보기: CRestrictions 클래스'
title: CRestrictions 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
helpviewer_keywords:
- CRestrictions class
- Open method
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
ms.openlocfilehash: 28eee2ea8d7e3b28edaab745c48426c878cc2f2d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170284"
---
# <a name="crestrictions-class"></a>CRestrictions 클래스

스키마 행 집합에 대 한 제한을 지정할 수 있는 제네릭 클래스입니다.

## <a name="syntax"></a>구문

```cpp
template <class T, short nRestrictions, const GUID* pguid>
class CRestrictions :
   public CSchemaRowset <T, nRestrictions>
```

### <a name="parameters"></a>매개 변수

*T*<br/>
접근자에 사용 되는 클래스입니다.

*nRestrictions 사항*<br/>
스키마 행 집합에 대 한 제한 열 수입니다.

*pguid*<br/>
스키마에 대 한 GUID에 대 한 포인터입니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldbsch.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[열기](#open)|사용자가 제공한 제한에 따라 결과 집합을 반환 합니다.|

## <a name="crestrictionsopen"></a><a name="open"></a> CRestrictions:: Open

사용자가 제공한 제한에 따라 결과 집합을 반환 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT Open(const CSession& session,
   LPCTSTR lpszParam 1 = NULL,
   LPCTSTR lpszParam 2 = NULL,
   LPCTSTR lpszParam 3 = NULL,
   LPCTSTR lpszParam 4 = NULL,
   LPCTSTR lpszParam 5 = NULL,
   LPCTSTR lpszParam 6 = NULL,
   LPCTSTR lpszParam 7 = NULL,
   bool bBind = true);
```

#### <a name="parameters"></a>매개 변수

*세션별*<br/>
진행 데이터 원본에 연결 하는 데 사용 되는 기존 세션 개체를 지정 합니다.

*lpszParam*<br/>
진행 스키마 행 집합에 대 한 제한을 지정 합니다.

*bBind*<br/>
진행 열 맵을 자동으로 바인딩할 지 여부를 지정 합니다. 기본값은입니다 **`true`** . 그러면 열 맵이 자동으로 바인딩됩니다. *Bbind* 를로 설정 하면 **`false`** 수동으로 바인딩할 수 있도록 열 맵의 자동 바인딩이 방지 됩니다. (수동 바인딩은 OLAP 사용자에 게 특히 관심이 있습니다.)

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

스키마 행 집합에 대해 최대 7 개의 제한을 지정할 수 있습니다.

각 스키마 행 집합에 대해 정의 된 제한 사항에 대 한 자세한 내용은 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[스키마 행 집합 클래스 및 Typedef 클래스](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)
