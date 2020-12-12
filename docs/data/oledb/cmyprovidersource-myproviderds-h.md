---
description: '자세히 알아보기: CCustomSource (CustomDS .h)'
title: CCustomSource(CustomDS.H)
ms.date: 10/22/2018
f1_keywords:
- myproviderds.h
- cmyprovidersource
- customds.h
- ccustomsource
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderSource class in MyProviderDS.H
- CCustomSource class in CustomDS.H
ms.assetid: c143d48e-59c8-4f67-9141-3aab51859b92
ms.openlocfilehash: 6fbb9fe0676521b01caa3bba5f5bb2be03d0fe6f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170440"
---
# <a name="ccustomsource-customdsh"></a>CCustomSource (CustomDS .h)

공급자 클래스는 여러 상속을 사용 합니다. 다음 코드는 데이터 원본 개체에 대 한 상속 체인을 보여 줍니다.

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSource
class ATL_NO_VTABLE CCustomSource :
   public CComObjectRootEx<CComSingleThreadModel>,
   public CComCoClass<CCustomSource, &CLSID_Custom>,
   public IDBCreateSessionImpl<CCustomSource, CCustomSession>,
   public IDBInitializeImpl<CCustomSource>,
   public IDBPropertiesImpl<CCustomSource>,
   public IPersistImpl<CCustomSource>,
   public IInternalConnectionImpl<CCustomSource>
```

모든 COM 구성 요소는 및에서 파생 `CComObjectRootEx` `CComCoClass` 됩니다. `CComObjectRootEx` 인터페이스에 대 한 모든 구현을 제공 합니다 `IUnknown` . 모든 스레딩 모델을 처리할 수 있습니다. `CComCoClass` 필요한 모든 오류 지원 기능을 처리 합니다. 보다 다양 한 오류 정보를 클라이언트에 전송 하려면의 오류 Api 중 일부를 사용할 수 있습니다 `CComCoClass` .

또한 데이터 소스 개체는 여러 ' 구현이 ' 클래스에서 상속 됩니다. 각 클래스는 인터페이스에 대 한 구현을 제공 합니다. 데이터 소스 개체는,, `IPersist` `IDBProperties` `IDBInitialize` 및 인터페이스를 구현 합니다 `IDBCreateSession` . 각 인터페이스는 OLE DB에서 데이터 원본 개체를 구현 하는 데 필요 합니다. 이러한 ' 구현이 ' 클래스 중 하나에서 상속 하거나 상속 하지 않으므로 특정 기능을 지원 하거나 지원 하지 않도록 선택할 수 있습니다. 인터페이스를 지원 하려는 경우 `IDBDataSourceAdmin` 클래스에서 상속 하 여 `IDBDataSourceAdminImpl` 필요한 기능을 얻을 수 있습니다.

## <a name="com-map"></a>COM 맵

클라이언트는 `QueryInterface` 데이터 소스의 인터페이스에 대해를 호출할 때마다 다음 COM 맵을 거칩니다.

```cpp
BEGIN_COM_MAP(CCustomSource)
   COM_INTERFACE_ENTRY(IDBCreateSession)
   COM_INTERFACE_ENTRY(IDBInitialize)
   COM_INTERFACE_ENTRY(IDBProperties)
   COM_INTERFACE_ENTRY(IPersist)
   COM_INTERFACE_ENTRY(IInternalConnection)
END_COM_MAP()
```

COM_INTERFACE_ENTRY 매크로는 ATL에서 제공 되며의 구현에서 `QueryInterface` `CComObjectRootEx` 적절 한 인터페이스를 반환 하도록 지시 합니다.

## <a name="property-map"></a>속성 맵

속성 맵은 공급자가 할당 한 모든 속성을 지정 합니다.

```cpp
BEGIN_PROPSET_MAP(CCustomSource)
   BEGIN_PROPERTY_SET(DBPROPSET_DATASOURCEINFO)
      PROPERTY_INFO_ENTRY(ACTIVESESSIONS)
      PROPERTY_INFO_ENTRY(ASYNCTXNABORT)
      PROPERTY_INFO_ENTRY(ASYNCTXNCOMMIT)
      PROPERTY_INFO_ENTRY(BYREFACCESSORS)
      PROPERTY_INFO_ENTRY_VALUE(CATALOGLOCATION, DBPROPVAL_CL_START)
      PROPERTY_INFO_ENTRY(CATALOGTERM)
      PROPERTY_INFO_ENTRY(CATALOGUSAGE)
      PROPERTY_INFO_ENTRY(COLUMNDEFINITION)
      PROPERTY_INFO_ENTRY(CONCATNULLBEHAVIOR)
      PROPERTY_INFO_ENTRY(DATASOURCENAME)
      PROPERTY_INFO_ENTRY(DATASOURCEREADONLY)
      PROPERTY_INFO_ENTRY(DBMSNAME)
      PROPERTY_INFO_ENTRY(DBMSVER)
      PROPERTY_INFO_ENTRY_VALUE(DSOTHREADMODEL, DBPROPVAL_RT_FREETHREAD)
      PROPERTY_INFO_ENTRY(GROUPBY)
      PROPERTY_INFO_ENTRY(HETEROGENEOUSTABLES)
      PROPERTY_INFO_ENTRY(IDENTIFIERCASE)
      PROPERTY_INFO_ENTRY(MAXINDEXSIZE)
      PROPERTY_INFO_ENTRY(MAXROWSIZE)
      PROPERTY_INFO_ENTRY(MAXROWSIZEINCLUDESBLOB)
      PROPERTY_INFO_ENTRY(MAXTABLESINSELECT)
      PROPERTY_INFO_ENTRY(MULTIPLEPARAMSETS)
      PROPERTY_INFO_ENTRY(MULTIPLERESULTS)
      PROPERTY_INFO_ENTRY(MULTIPLESTORAGEOBJECTS)
      PROPERTY_INFO_ENTRY(MULTITABLEUPDATE)
      PROPERTY_INFO_ENTRY(NULLCOLLATION)
      PROPERTY_INFO_ENTRY(OLEOBJECTS)
      PROPERTY_INFO_ENTRY(ORDERBYCOLUMNSINSELECT)
      PROPERTY_INFO_ENTRY(OUTPUTPARAMETERAVAILABILITY)
      PROPERTY_INFO_ENTRY(PERSISTENTIDTYPE)
      PROPERTY_INFO_ENTRY(PREPAREABORTBEHAVIOR)
      PROPERTY_INFO_ENTRY(PREPARECOMMITBEHAVIOR)
      PROPERTY_INFO_ENTRY(PROCEDURETERM)
      PROPERTY_INFO_ENTRY(PROVIDERNAME)
      PROPERTY_INFO_ENTRY(PROVIDEROLEDBVER)
      PROPERTY_INFO_ENTRY(PROVIDERVER)
      PROPERTY_INFO_ENTRY(QUOTEDIDENTIFIERCASE)
      PROPERTY_INFO_ENTRY(ROWSETCONVERSIONSONCOMMAND)
      PROPERTY_INFO_ENTRY(SCHEMATERM)
      PROPERTY_INFO_ENTRY(SCHEMAUSAGE)
      PROPERTY_INFO_ENTRY(STRUCTUREDSTORAGE)
      PROPERTY_INFO_ENTRY(SUBQUERIES)
      PROPERTY_INFO_ENTRY(TABLETERM)
      PROPERTY_INFO_ENTRY(USERNAME)
   END_PROPERTY_SET(DBPROPSET_DATASOURCEINFO)
   BEGIN_PROPERTY_SET(DBPROPSET_DBINIT)
      PROPERTY_INFO_ENTRY(AUTH_PASSWORD)
      PROPERTY_INFO_ENTRY(AUTH_PERSIST_SENSITIVE_AUTHINFO)
      PROPERTY_INFO_ENTRY(AUTH_USERID)
      PROPERTY_INFO_ENTRY(INIT_DATASOURCE)
      PROPERTY_INFO_ENTRY(INIT_HWND)
      PROPERTY_INFO_ENTRY(INIT_LCID)
      PROPERTY_INFO_ENTRY(INIT_LOCATION)
      PROPERTY_INFO_ENTRY(INIT_MODE)
      PROPERTY_INFO_ENTRY(INIT_PROMPT)
      PROPERTY_INFO_ENTRY(INIT_PROVIDERSTRING)
      PROPERTY_INFO_ENTRY(INIT_TIMEOUT)
   END_PROPERTY_SET(DBPROPSET_DBINIT)
   BEGIN_PROPERTY_SET(DBPROPSET_DATASOURCE)
      PROPERTY_INFO_ENTRY(CURRENTCATALOG)
   END_PROPERTY_SET(DBPROPSET_DATASOURCE)
   CHAIN_PROPERTY_SET(CCustomSession)
END_PROPSET_MAP()
```

OLE DB의 속성은 그룹화 되어 있습니다. 데이터 원본 개체에는 두 개의 속성 그룹 (DBPROPSET_DATASOURCEINFO 집합에 대 한 속성 하나 및 DBPROPSET_DBINIT 집합에 대 한 속성)이 있습니다. DBPROPSET_DATASOURCEINFO 집합은 공급자 및 해당 데이터 소스에 대 한 속성에 해당 합니다. DBPROPSET_DBINIT 집합은 초기화에 사용 되는 속성에 해당 합니다. OLE DB 공급자 템플릿은 PROPERTY_SET 매크로를 사용 하 여 이러한 집합을 처리 합니다. 매크로는 속성의 배열을 포함 하는 블록을 만듭니다. 클라이언트가 인터페이스를 호출할 때마다 `IDBProperties` 공급자는 속성 맵을 사용 합니다.

사양의 모든 속성을 구현할 필요는 없습니다. 그러나 필수 속성을 지원 해야 합니다. 자세한 내용은 수준 0 규칙 사양을 참조 하세요. 속성을 지원 하지 않으려면 맵에서 제거할 수 있습니다. 속성을 지원 하려는 경우 PROPERTY_INFO_ENTRY 매크로를 사용 하 여 맵에 추가 합니다. 매크로는 `UPROPINFO` 다음 코드와 같이 구조에 해당 합니다.

```cpp
struct UPROPINFO
{
   DBPROPID    dwPropId;
   ULONG       ulIDS;
   VARTYPE     VarType;
   DBPROPFLAGS dwFlags;
   union
   {
      DWORD dwVal;
      LPOLESTR szVal;
   };
   DBPROPOPTIONS dwOption;
};
```

구조체의 각 요소는 속성을 처리 하기 위한 정보를 나타냅니다. 여기에는 `DBPROPID` 속성에 대 한 GUID 및 ID를 결정 하는가 포함 됩니다. 또한 속성의 형식 및 값을 확인 하는 항목을 포함 합니다.

속성의 기본값을 변경 하려는 경우 (소비자는 언제 든 지 쓰기 가능 속성의 값을 변경할 수 있음) PROPERTY_INFO_ENTRY_VALUE 또는 PROPERTY_INFO_ENTRY_EX 매크로를 사용할 수 있습니다. 이러한 매크로를 사용 하 여 해당 속성에 대 한 값을 지정할 수 있습니다. PROPERTY_INFO_ENTRY_VALUE 매크로는 값을 변경할 수 있는 약식 표기법입니다. PROPERTY_INFO_ENTRY_VALUE 매크로는 PROPERTY_INFO_ENTRY_EX 매크로를 호출 합니다. 이 매크로를 사용 하 여 구조체의 모든 특성을 추가 하거나 변경할 수 있습니다 `UPROPINFO` .

고유한 속성 집합을 정의 하려면 추가 BEGIN_PROPSET_MAP/END_PROPSET_MAP 조합을 만들어 하나를 추가할 수 있습니다. 속성 집합에 대 한 GUID를 정의한 다음 고유한 속성을 정의 합니다. 공급자별 속성을 사용 하는 경우 기존 속성을 사용 하는 대신 새 속성 집합에 추가 합니다. 이는 OLE DB의 이후 버전에서 발생 하는 문제를 방지 합니다.

## <a name="user-defined-property-sets"></a>User-Defined 속성 집합

Visual C++는 사용자 정의 속성 집합을 지원 합니다. 또는를 재정의할 필요가 없습니다 `GetProperties` `GetPropertyInfo` . 대신, 템플릿에서 사용자 정의 속성 집합을 검색 하 여 해당 개체에 추가 합니다.

초기화 시에 사용할 수 있어야 하는 사용자 정의 속성 집합을 사용 하는 경우 (즉, 소비자가를 호출 하기 전에 `IDBInitialize::Initialize` ) BEGIN_PROPERTY_SET_EX 매크로와 함께 UPROPSET_USERINIT 플래그를 사용 하 여 지정할 수 있습니다. 이 속성이 작동 하려면 (OLE DB 사양에 필요 함) 데이터 소스 개체에 속성 집합이 있어야 합니다. 예를 들어:

```cpp
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)
```

## <a name="see-also"></a>참고 항목

[공급자 Wizard-Generated 파일](../../data/oledb/provider-wizard-generated-files.md)<br/>
