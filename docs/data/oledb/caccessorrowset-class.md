---
title: CAccessorRowset 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CAccessorRowset
- ATL.CAccessorRowset
- ATL::CAccessorRowset
- CAccessorRowset.Bind
- CAccessorRowset::Bind
- CAccessorRowset::CAccessorRowset
- CAccessorRowset.CAccessorRowset
- CAccessorRowset
- ATL.CAccessorRowset.CAccessorRowset
- ATL::CAccessorRowset::CAccessorRowset
- CAccessorRowset.Close
- CAccessorRowset::Close
- CAccessorRowset::FreeRecordMemory
- CAccessorRowset.FreeRecordMemory
- FreeRecordMemory
- GetColumnInfo
- CAccessorRowset.GetColumnInfo
- CAccessorRowset::GetColumnInfo
dev_langs:
- C++
helpviewer_keywords:
- CAccessorRowset class
- CAccessorRowset class, methods
- CAccessorRowset class, members
- Bind method
- CAccessorRowset class, constructor
- Close method
- FreeRecordMemory method
- GetColumnInfo method
ms.assetid: bd4f58ed-cebf-4d43-8985-1e5fcbf06953
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 85f08ae7a996a762be915bcce820c33a0a8e549c
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572270"
---
# <a name="caccessorrowset-class"></a>CAccessorRowset 클래스
행 집합 및 연결 된 해당 접근자 단일 클래스에 캡슐화합니다.  
  
## <a name="syntax"></a>구문

```cpp
template <class TAccessor = CNoAccessor, 
   template <typename T> class TRowset = CRowset>  
class CAccessorRowset : public TAccessor, public TRowset<TAccessor>  
```  
  
### <a name="parameters"></a>매개 변수  
 *TAccessor*  
 접근자 클래스입니다.  
  
 *TRowset*  
 행 집합 클래스입니다.  

## <a name="requirements"></a>요구 사항  
 **헤더:** atldbcli.h  
  
## <a name="members"></a>멤버  
  
### <a name="methods"></a>메서드  
  
|||  
|-|-|  
|[바인딩](#bind)|바인딩을 만듭니다 (때 사용한 `bBind` 으로 지정 됩니다 **false** 에서 [ccommand:: Open](../../data/oledb/ccommand-open.md)).|  
|[CAccessorRowset](#caccessorrowset)|생성자입니다.|  
|[닫기](#close)|행 집합 및 모든 접근자를 닫습니다.|  
|[FreeRecordMemory](#freerecordmemory)|해제 해야 하는 현재 레코드의 모든 열을 해제 합니다.|  
|[GetColumnInfo](#getcolumninfo)|구현 [icolumnsinfo:: Getcolumninfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))합니다.|  
  
## <a name="remarks"></a>설명  
 클래스 `TAccessor` 접근자를 관리 합니다. 클래스 *TRowset* 행 집합을 관리 합니다.  

## <a name="bind"></a> Caccessorrowset:: Bind
지정한 경우 바인딩을 만듭니다 `bBind` 으로 **false** 에서 [ccommand:: Open](../../data/oledb/ccommand-open.md)합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp
HRESULT Bind();  
```  
  
### <a name="return-value"></a>반환 값  
 표준 HRESULT입니다.  

## <a name="caccessorrowset"></a> Caccessorrowset:: Caccessorrowset
초기화는 `CAccessorRowset` 개체입니다.  
  
### <a name="syntax"></a>구문  
  
```cpp
CAccessorRowset();  
```  

## <a name="close"></a> Caccessorrowset:: Close
모든 활성 접근자 및 행 집합을 해제합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp
void Close();  
```  
  
### <a name="remarks"></a>설명  
 관련 된 모든 메모리를 해제합니다.  

## <a name="freerecordmemory"></a> Caccessorrowset:: Freerecordmemory
해제 해야 하는 현재 레코드의 모든 열을 해제 합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp
void FreeRecordMemory();  
```  

## <a name="getcolumninfo"></a> Caccessorrowset:: Getcolumninfo
열린된 행 집합에서 열 정보를 가져옵니다.  
  
### <a name="syntax"></a>구문  
  
```cpp
HRESULT GetColumnInfo(DBORDINAL* pulColumns, 
   DBCOLUMNINFO** ppColumnInfo, 
   LPOLESTR* ppStrings) const; 
    
HRESULT GetColumnInfo(DBORDINAL* pColumns, 
   DBCOLUMNINFO** ppColumnInfo);  
```  
  
#### <a name="parameters"></a>매개 변수  
 참조 [icolumnsinfo:: Getcolumninfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) 에 *OLE DB Programmer's Reference*합니다.  
  
### <a name="return-value"></a>반환 값  
 표준 HRESULT입니다.  
  
### <a name="remarks"></a>설명  
 사용자는 반환 된 열 정보와 문자열 버퍼를 해제 해야 합니다. 사용 하는 경우이 메서드의 두 번째 버전을 사용 하 여 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) 바인딩을 재정의 해야 합니다.  
  
 자세한 내용은 [icolumnsinfo:: Getcolumninfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) 에 *OLE DB Programmer's Reference*합니다.  
  
## <a name="see-also"></a>참고 항목  
 [OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)