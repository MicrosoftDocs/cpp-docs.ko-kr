---
title: CManualAccessor 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CManualAccessor
- ATL.CManualAccessor
- CManualAccessor
- ATL::CManualAccessor::AddBindEntry
- ATL.CManualAccessor.AddBindEntry
- CManualAccessor::AddBindEntry
- AddBindEntry
- CManualAccessor.AddBindEntry
- CManualAccessor::AddParameterEntry
- ATL.CManualAccessor.AddParameterEntry
- CManualAccessor.AddParameterEntry
- AddParameterEntry
- ATL::CManualAccessor::AddParameterEntry
- ATL::CManualAccessor::CreateAccessor
- CreateAccessor
- ATL.CManualAccessor.CreateAccessor
- CManualAccessor.CreateAccessor
- CManualAccessor::CreateAccessor
- ATL::CManualAccessor::CreateParameterAccessor
- ATL.CManualAccessor.CreateParameterAccessor
- CManualAccessor.CreateParameterAccessor
- CreateParameterAccessor
- CManualAccessor::CreateParameterAccessor
dev_langs:
- C++
helpviewer_keywords:
- CManualAccessor class
- AddBindEntry method
- AddParameterEntry method
- CreateAccessor method
- CreateParameterAccessor method
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9b0cf71ce31d9f4d96d2064ebafd28b7ea5ff70d
ms.sourcegitcommit: b217daee32d3413cf33753d9b4dc35a0022b1bfa
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233471"
---
# <a name="cmanualaccessor-class"></a>CManualAccessor 클래스
고급 사용을 위한 접근자 유형을 나타냅니다.  
  
## <a name="syntax"></a>구문

```cpp
class CManualAccessor : public CAccessorBase  
```  

## <a name="requirements"></a>요구 사항  
 **헤더:** atldbcli.h  
  
## <a name="members"></a>멤버  
  
### <a name="methods"></a>메서드  
  
|||  
|-|-|  
|[AddBindEntry](#addbindentry)|출력 열에 바인딩 항목을 추가합니다.|  
|[AddParameterEntry](#addparameterentry)|매개 변수 접근자에 매개 변수 항목을 추가합니다.|  
|[CreateAccessor](#createaccessor)|바인딩 구조 열에 대 한 메모리를 할당 하 고 열 데이터 멤버를 초기화 합니다.|  
|[CreateParameterAccessor](#createparameteraccessor)|바인딩 구조를 매개 변수에 대 한 메모리를 할당 하 고 매개 변수 데이터 멤버를 초기화 합니다.|  
  
## <a name="remarks"></a>설명  
 사용 하 여 `CManualAccessor`, 런타임 함수 호출에 의해 출력 되는 열 바인딩 및 매개 변수를 지정할 수 있습니다.  

## <a name="addbindentry"></a> Cmanualaccessor:: Addbindentry
출력 열에 바인딩 항목을 추가합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp
void AddBindEntry(DBORDINAL nOrdinal,  
   DBTYPE wType,  DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL) throw ();  
```  
  
#### <a name="parameters"></a>매개 변수  
 참조 [DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx) 에 *OLE DB Programmer's Reference*합니다.  
  
 *nOrdinal*  
 [in] 열 번호입니다.  
  
 *wType*  
 [in] 데이터 형식입니다.  
  
 *nColumnSize*  
 [in] 열 크기 (바이트)에서입니다.  
  
 *pData*  
 [in] 버퍼에 저장 된 열 데이터에 대 한 포인터입니다.  
  
 *두*  
 [in] 필요한 경우 필드 길이에 대 한 포인터입니다.  
  
 *pStatus*  
 [in] 필요한 경우 열 상태에 바인딩할 변수의 포인터입니다.  
  
### <a name="remarks"></a>설명  
 이 함수를 사용 하려면 먼저 불러와야 [CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)합니다. 에 지정 된 열의 수보다 더 많은 항목을 추가할 수 없습니다 `CreateAccessor`합니다. 
  
## <a name="addparameterentry"></a> Cmanualaccessor:: Addparameterentry
매개 변수 입력 구조에 매개 변수 항목을 추가합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp
void AddParameterEntry(DBORDINAL nOrdinal,  
   DBTYPE wType,  DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL,  
   DBPARAMIO eParamIO = DBPARAMIO_INPUT) throw ();  
```  
  
#### <a name="parameters"></a>매개 변수  
 참조 [DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx) 에 *OLE DB Programmer's Reference*합니다.  
  
 *nOrdinal*  
 [in] 매개 변수 수입니다.  
  
 *wType*  
 [in] 데이터 형식입니다.  
  
 *nColumnSize*  
 [in] 열 크기 (바이트)에서입니다.  
  
 *pData*  
 [in] 버퍼에 저장 된 열 데이터에 대 한 포인터입니다.  
  
 *두*  
 [in] 필요한 경우 필드 길이에 대 한 포인터입니다.  
  
 *pStatus*  
 [in] 필요한 경우 열 상태에 바인딩할 변수의 포인터입니다.  
  
 *eParamIO*  
 [in] 바인딩에 연결 된 매개 변수는 입력, 입/출력 또는 출력 매개 변수 인지 여부를 지정 합니다.  
  
### <a name="remarks"></a>설명  
 이 함수를 사용 하려면 먼저 불러와야 [CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md)합니다. 

## <a name="createaccessor"></a> Cmanualaccessor:: Createaccessor
바인딩 구조 열에 대 한 메모리를 할당 하 고 열 데이터 멤버를 초기화 합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp
HRESULT CreateAccessor(int nBindEntries,   
  void* pBuffer,   
   DBLENGTH nBufferSize) throw();  
```  
  
#### <a name="parameters"></a>매개 변수  
 *nBindEntries*  
 [in] 열의 수입니다. 이 수에 대 한 호출의 수와 일치 해야 합니다 [cmanualaccessor:: Addbindentry](../../data/oledb/cmanualaccessor-addbindentry.md) 함수입니다.  
  
 *pBuffer*  
 [in] 출력 열에는 저장 된 버퍼에 대 한 포인터입니다.  
  
 *nBufferSize*  
 [in] 바이트 버퍼의 크기입니다.  
  
### <a name="return-value"></a>반환 값  
 HRESULT 값 중 하나입니다.  
  
### <a name="remarks"></a>설명  
 이 함수를 호출 하기 전에 호출 된 `CManualAccessor::AddBindEntry` 함수입니다.  

## <a name="createparameteraccessor"></a> Cmanualaccessor:: Createparameteraccessor
바인딩 구조를 매개 변수에 대 한 메모리를 할당 하 고 매개 변수 데이터 멤버를 초기화 합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp
HRESULT CreateParameterAccessor(int nBindEntries,   
  void* pBuffer,   
   DBLENGTH nBufferSize) throw();  
```  
  
#### <a name="parameters"></a>매개 변수  
 *nBindEntries*  
 [in] 열의 수입니다.  
  
 *pBuffer*  
 [in] 입력된 열에는 저장 된 버퍼에 대 한 포인터입니다.  
  
 *nBufferSize*  
 [in] 바이트 버퍼의 크기입니다.  
  
### <a name="return-value"></a>반환 값  
 HRESULT 값 중 하나입니다.  
  
### <a name="remarks"></a>설명  
 이 함수를 호출 하기 전에 호출 해야 합니다 [AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)합니다.

## <a name="see-also"></a>참고 항목  
 [DBViewer](../../visual-cpp-samples.md)   
 [OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 클래스](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor 클래스](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicParameterAccessor 클래스](../../data/oledb/cdynamicparameteraccessor-class.md)