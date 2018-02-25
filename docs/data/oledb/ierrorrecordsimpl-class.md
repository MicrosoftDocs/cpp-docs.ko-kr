---
title: "IErrorRecordsImpl 클래스 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::IErrorRecordsImpl
- ATL.IErrorRecordsImpl
- IErrorRecordsImpl
dev_langs:
- C++
helpviewer_keywords:
- IErrorRecordsImpl class
ms.assetid: dea8e938-c5d8-45ab-86de-eb8fbf534ffb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f3d466cbf761342706774a9b5a52c5b4e69a7328
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="ierrorrecordsimpl-class"></a>IErrorRecordsImpl 클래스
OLE DB 구현 [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx) 레코드를 추가 하 고 데이터 멤버에서 레코드를 검색 하는 인터페이스 ([m_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)) 형식의 **CAtlArray <** `RecordClass`**>**.  
  
## <a name="syntax"></a>구문

```cpp
template <class T, class RecordClass = ATLERRORINFO>  
class IErrorRecordsImpl : public IErrorRecords  
```  
  
#### <a name="parameters"></a>매개 변수  
 `T`  
 클래스에서 파생 `IErrorRecordsImpl`합니다.  
  
 `RecordClass`  
 OLE DB 오류 개체를 나타내는 클래스입니다.  
  
## <a name="members"></a>멤버  
  
### <a name="methods"></a>메서드  
  
|||  
|-|-|  
|[GetErrorDescriptionString](../../data/oledb/ierrorrecordsimpl-geterrordescriptionstring.md)|오류 레코드에서 오류 설명 문자열을 가져옵니다.|  
|[GetErrorGUID](../../data/oledb/ierrorrecordsimpl-geterrorguid.md)|오류 레코드에서 오류를 GUID를 가져옵니다.|  
|[GetErrorHelpContext](../../data/oledb/ierrorrecordsimpl-geterrorhelpcontext.md)|오류 레코드에서 도움말 컨텍스트 ID를 가져옵니다.|  
|[GetErrorHelpFile](../../data/oledb/ierrorrecordsimpl-geterrorhelpfile.md)|오류 레코드에서 도움말 파일의 전체 경로 이름을 가져옵니다.|  
|[GetErrorSource](../../data/oledb/ierrorrecordsimpl-geterrorsource.md)|오류 레코드에서 오류 소스 코드를 가져옵니다.|  
  
### <a name="interface-methods"></a>인터페이스 메서드  
  
|||  
|-|-|  
|[AddErrorRecord](../../data/oledb/ierrorrecordsimpl-adderrorrecord.md)|OLE DB 오류 개체에 레코드를 추가합니다.|  
|[GetBasicErrorInfo](../../data/oledb/cdberrorinfo-getbasicerrorinfo.md)|반환 코드 및 공급자 특정 오류 번호와 같은 오류에 대 한 기본 정보를 반환 합니다.|  
|[GetCustomErrorObject](../../data/oledb/cdberrorinfo-getcustomerrorobject.md)|사용자 지정 오류 개체에는 인터페이스에 대 한 포인터를 반환합니다.|  
|[GetErrorInfo](../../data/oledb/cdberrorinfo-geterrorinfo.md)|반환 된 [IErrorInfo](https://msdn.microsoft.com/en-us/library/ms718112.aspx) 지정된 된 레코드에 대 한 인터페이스 포인터입니다.|  
|[GetErrorParameters](../../data/oledb/cdberrorinfo-geterrorparameters.md)|오류 매개 변수를 반환합니다.|  
|[GetRecordCount](../../mfc/reference/cdaorecordset-class.md#getrecordcount)|OLE DB 레코드 개체의 레코드 수를 반환 합니다.|  
  
### <a name="data-members"></a>데이터 멤버  
  
|||  
|-|-|  
|[m_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)|오류 레코드의 배열입니다.|  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atldb.h  
  
## <a name="see-also"></a>참고 항목  
 [OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 공급자 템플릿 구조](../../data/oledb/ole-db-provider-template-architecture.md)