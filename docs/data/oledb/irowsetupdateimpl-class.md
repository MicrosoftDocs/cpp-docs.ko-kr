---
title: IRowsetUpdateImpl 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
- SetData
- IRowsetUpdateImpl::SetData
- IRowsetUpdateImpl.SetData
- ATL::IRowsetUpdateImpl::SetData
- ATL.IRowsetUpdateImpl.SetData
- ATL.IRowsetUpdateImpl.GetOriginalData
- IRowsetUpdateImpl.GetOriginalData
- GetOriginalData
- ATL::IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetPendingRows
- GetPendingRows
- IRowsetUpdateImpl.GetPendingRows
- ATL::IRowsetUpdateImpl::GetPendingRows
- ATL.IRowsetUpdateImpl.GetPendingRows
- ATL.IRowsetUpdateImpl.GetRowStatus
- IRowsetUpdateImpl::GetRowStatus
- IRowsetUpdateImpl.GetRowStatus
- ATL::IRowsetUpdateImpl::GetRowStatus
- GetRowStatus
- ATL.IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Update
- IRowsetUpdateImpl::Update
- IRowsetUpdateImpl.Update
- ATL.IRowsetUpdateImpl.Update
- IRowsetUpdateImpl::IsUpdateAllowed
- IRowsetUpdateImpl.IsUpdateAllowed
- IsUpdateAllowed
- IRowsetUpdateImpl.m_mapCachedData
- IRowsetUpdateImpl::m_mapCachedData
- m_mapCachedData
dev_langs:
- C++
helpviewer_keywords:
- providers, updatable
- IRowsetUpdateImpl class
- updatable providers, deferred update
- SetData method
- GetOriginalData method
- GetPendingRows method
- GetRowStatus method
- Undo method
- Update method
- IsUpdateAllowed method
- m_mapCachedData
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: afbf8b42b4d518412c1004d78c5c718e54078c1c
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340783"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl 클래스
OLE DB 템플릿 구현의 합니다 [IRowsetUpdate](https://msdn.microsoft.com/library/ms714401.aspx) 인터페이스입니다.  
  
## <a name="syntax"></a>구문

```cpp
template <  
   class T,   
   class Storage,   
   class UpdateArray = CAtlArray<Storage>,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>   
>  

class IRowsetUpdateImpl : public IRowsetChangeImpl<  
   T,   
   Storage,   
   IRowsetUpdate,   
   RowClass,   
   MapClass>  
```  
  
### <a name="parameters"></a>매개 변수  
 *T*  
 파생 된 클래스 `IRowsetUpdateImpl`합니다.  
  
 *저장소*  
 사용자 레코드입니다.  
  
 *UpdateArray*  
 행 집합을 업데이트 하는 캐시 된 데이터가 들어 있는 배열입니다.  
  
 *RowClass*  
 에 대 한 저장소 단위는 `HROW`합니다.  
  
 *MapClass*  
 공급자가 보유 하는 모든 행 핸들에 대 한 저장소 단위입니다.  

## <a name="requirements"></a>요구 사항  
 **헤더:** atldb.h  
  
## <a name="members"></a>멤버  
  
### <a name="interface-methods-used-with-irowsetchange"></a>인터페이스 메서드 (IRowsetChange와 함께 사용)  
  
|||  
|-|-|  
|[SetData](#setdata)|하나 이상의 열에 데이터 값을 설정 합니다.|  
  
### <a name="interface-methods-used-with-irowsetupdate"></a>인터페이스 메서드 (IRowsetUpdate와 함께 사용)  
  
|||  
|-|-|  
|[GetOriginalData](#getoriginaldata)|가장 최근에 전송 또는 보류 중인 변경 내용을 무시 하 고 해당 데이터 원본에서 가져온 데이터를 가져옵니다.|  
|[GetPendingRows](#getpendingrows)|보류 중인 변경 내용 사용 하 여 행의 목록을 반환합니다.|  
|[GetRowStatus](#getrowstatus)|지정 된 행의 상태를 반환 합니다.|  
|[실행 취소](#undo)|마지막 페치 또는 업데이트 이후 행 변경 내용을 실행 취소합니다.|  
|[업데이트](#update)|마지막 페치 또는 업데이트 이후 행에 대해 변경 내용을 전송 합니다.|  
  
### <a name="implementation-methods-callback"></a>구현 메서드 (콜백)  
  
|||  
|-|-|  
|[IsUpdateAllowed](#isupdateallowed)|업데이트를 허용 하기 전에 등 보안상의 무결성을 확인 하는 데 사용 합니다.|  
  
### <a name="data-members"></a>데이터 멤버  
  
|||  
|-|-|  
|[m_mapCachedData](#mapcacheddata)|지연 된 작업에 대 한 원래 데이터를 포함합니다.|  
  
## <a name="remarks"></a>설명  
 먼저 읽고 이해에 대 한 설명서 [IRowsetChange](https://msdn.microsoft.com/library/ms715790.aspx)이므로 방식도 설명 되어 모든도 여기서 적용 됩니다. 6 장도 읽어 보아야 합니다 *OLE DB Programmer's Reference* 데이터를 설정 합니다.  
  
 `IRowsetUpdateImpl` OLE DB 구현 `IRowsetUpdate` 전송을 사용 하 여 변경 내용 지연 하는 소비자를 사용 하도록 설정 하는 인터페이스 `IRowsetChange` 를 데이터 원본 및 전송 하기 전에 변경 내용을 취소 합니다.  
  
> [!IMPORTANT]
>  공급자를 구현 하기 전에 다음 설명서를 참조 하는 것이 좋습니다.  
  
-   [업데이트 가능 공급자 만들기](../../data/oledb/creating-an-updatable-provider.md)  
  
-   6 장은 *OLE DB 프로그래머 참조*  
  
-   또한 참조 하는 방법을 `RUpdateRowset` 클래스 UpdatePV 샘플에서 사용 됩니다  

## <a name="setdata"></a> Irowsetupdateimpl:: Setdata
하나 이상의 열에 데이터 값을 설정 합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp
STDMETHOD (SetData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData);  
```  
  
#### <a name="parameters"></a>매개 변수  
 참조 [irowsetchange:: Setdata](https://msdn.microsoft.com/library/ms721232.aspx) 에 *OLE DB Programmer's Reference*합니다.  
  
### <a name="remarks"></a>설명  
 이 메서드를 재정의 합니다 [irowsetchangeimpl:: Setdata](../../data/oledb/irowsetchangeimpl-setdata.md) 메서드에 하지만, 작업을 즉시 또는 지연 된 처리를 허용 하도록 원본 데이터의 캐싱을 포함 됩니다.

## <a name="getoriginaldata"></a> Irowsetupdateimpl:: Getoriginaldata
가장 최근에 전송 또는 보류 중인 변경 내용을 무시 하 고 해당 데이터 원본에서 가져온 데이터를 가져옵니다.  
  
### <a name="syntax"></a>구문  
  
```cpp
STDMETHOD (GetOriginalData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pData);  
```  
  
#### <a name="parameters"></a>매개 변수  
 참조 [IRowsetUpdate::GetOriginalData](https://msdn.microsoft.com/library/ms709947.aspx) 에 *OLE DB Programmer's Reference*합니다.   

## <a name="getpendingrows"></a> Irowsetupdateimpl:: Getpendingrows
보류 중인 변경 내용 사용 하 여 행의 목록을 반환합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp
STDMETHOD (GetPendingRows )(HCHAPTER /* hReserved */,  
   DBPENDINGSTATUS dwRowStatus,  
   DBCOUNTITEM* pcPendingRows,  
   HROW** prgPendingRows,  
   DBPENDINGSTATUS** prgPendingStatus);  
```  
  
#### <a name="parameters"></a>매개 변수  
 *hReserved*  
 [in] 에 해당 하는 *hChapter* 에 매개 변수 [IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/library/ms719626.aspx)합니다.  
  
 다른 매개 변수를 참조 하세요 [IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/library/ms719626.aspx) 에 *OLE DB Programmer's Reference*합니다.  
  
### <a name="remarks"></a>설명  
 자세한 내용은 [IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/library/ms719626.aspx) 에 *OLE DB Programmer's Reference*합니다.  

## <a name="getrowstatus"></a> Irowsetupdateimpl:: Getrowstatus
지정 된 행의 상태를 반환 합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp
STDMETHOD (GetRowStatus )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBPENDINGSTATUS rgPendingStatus[]);  
```  
  
#### <a name="parameters"></a>매개 변수  
 *hReserved*  
 [in] 에 해당 하는 *hChapter* 에 매개 변수 [IRowsetUpdate::GetRowStatus](https://msdn.microsoft.com/library/ms724377.aspx)합니다.  
  
 다른 매개 변수를 참조 하세요 [IRowsetUpdate::GetRowStatus](https://msdn.microsoft.com/library/ms724377.aspx) 에 *OLE DB Programmer's Reference*합니다.  

## <a name="undo"></a> Irowsetupdateimpl:: Undo
마지막 페치 또는 업데이트 이후 행 변경 내용을 실행 취소합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp
STDMETHOD (Undo )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[ ],  
   DBCOUNTITEM* pcRowsUndone,  
   HROW** prgRowsUndone,  
   DBROWSTATUS** prgRowStatus);  
```  
  
#### <a name="parameters"></a>매개 변수  
 *hReserved*  
 [in] 에 해당 하는 *hChapter* 에 매개 변수 [IRowsetUpdate::Undo](https://msdn.microsoft.com/library/ms719655.aspx)합니다.  
  
 *pcRowsUndone*  
 [out] 에 해당 하는 *pcRows* 에 매개 변수 [IRowsetUpdate::Undo](https://msdn.microsoft.com/library/ms719655.aspx)합니다.  
  
 *prgRowsUndone*  
 [in] 에 해당 하는 *prgRows* 에 매개 변수 [IRowsetUpdate::Undo](https://msdn.microsoft.com/library/ms719655.aspx)합니다.  
  
 다른 매개 변수를 참조 하세요 [IRowsetUpdate::Undo](https://msdn.microsoft.com/library/ms719655.aspx) 에 *OLE DB Programmer's Reference*합니다. 

## <a name="update"></a> Irowsetupdateimpl:: Update
마지막 페치 또는 업데이트 이후 행에 대해 변경 내용을 전송 합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp
STDMETHOD (Update )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBCOUNTITEM* pcRows,  
   HROW** prgRows,  
   DBROWSTATUS** prgRowStatus);  
```  
  
#### <a name="parameters"></a>매개 변수  
 *hReserved*  
 [in] 에 해당 하는 *hChapter* 에 매개 변수 [irowsetupdate:: Update](https://msdn.microsoft.com/library/ms719709.aspx)합니다.  
  
 다른 매개 변수를 참조 하세요 [irowsetupdate:: Update](https://msdn.microsoft.com/library/ms719709.aspx) 에 *OLE DB Programmer's Reference*합니다.  
  
### <a name="remarks"></a>설명  
 호출 하 여 변경 내용이 전송 [irowsetchangeimpl:: Flushdata](../../data/oledb/irowsetchangeimpl-flushdata.md)합니다. 소비자를 호출 해야 합니다 [crowset:: Update](../../data/oledb/crowset-update.md) 변경 내용을 적용 하려면. 설정할 *prgRowstatus* 에 설명 된 대로 적절 한 값 [행 상태](https://msdn.microsoft.com/library/ms722752.aspx) 에 *OLE DB Programmer's Reference*합니다. 
  
## <a name="isupdateallowed"></a> Irowsetupdateimpl:: Isupdateallowed
보안을 업데이트 하기 전에 등의 무결성을 확인 하려면이 메서드를 재정의 합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,  
   HROW /* [in] */ /* hRowUpdate */,  
   DBROWSTATUS* /* [out] */ /* pRowStatus */);  
```  
  
#### <a name="parameters"></a>매개 변수  
 *status*  
 [in] 행에 대 한 작업 보류 중 상태입니다.  
  
 *hRowUpdate*  
 [in] 사용자가 업데이트 하려는 행에 대 한 핸들입니다.  
  
 *pRowStatus*  
 [out] 사용자에 게 반환 상태입니다.  
  
### <a name="remarks"></a>설명  
 업데이트 허용 되어야 하 고 판단 하는 경우 S_OK;를 반환 합니다. 그렇지 않으면 E_FAIL을 반환합니다. 업데이트를 허용 하면도 설정 해야 합니다 `DBROWSTATUS` 에 [irowsetupdateimpl:: Update](../../data/oledb/irowsetupdateimpl-update.md) 를 적절 한 [행 상태](https://msdn.microsoft.com/library/ms722752.aspx)합니다.  

## <a name="mapcacheddata"></a> Irowsetupdateimpl:: M_mapcacheddata
지연 된 작업에 대 한 원래 데이터를 포함 하는 맵.  
  
### <a name="syntax"></a>구문  
  
```cpp
CAtlMap<   
   HROW hRow,    
   Storage* pData   
>   
m_mapCachedData;  
```  
  
#### <a name="parameters"></a>매개 변수  
 *hRow*  
 데이터에 대 한 행에 대 한 핸들입니다.  
  
 *pData*  
 데이터를 캐시에 대 한 포인터입니다. 형식의 데이터가 *저장소* (사용자 레코드 클래스). 참조 된 *저장소* 템플릿 인수 [IRowsetUpdateImpl 클래스](../../data/oledb/irowsetupdateimpl-class.md)합니다.  

## <a name="see-also"></a>참고 항목  
 [OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 공급자 템플릿 구조](../../data/oledb/ole-db-provider-template-architecture.md)   
 [업데이트 가능 공급자 만들기](../../data/oledb/creating-an-updatable-provider.md)