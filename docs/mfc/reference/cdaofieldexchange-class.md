---
title: CDaoFieldExchange 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoFieldExchange
- AFXDAO/CDaoFieldExchange
- AFXDAO/CDaoFieldExchange::IsValidOperation
- AFXDAO/CDaoFieldExchange::SetFieldType
- AFXDAO/CDaoFieldExchange::m_nOperation
- AFXDAO/CDaoFieldExchange::m_prs
dev_langs:
- C++
helpviewer_keywords:
- CDaoFieldExchange [MFC], IsValidOperation
- CDaoFieldExchange [MFC], SetFieldType
- CDaoFieldExchange [MFC], m_nOperation
- CDaoFieldExchange [MFC], m_prs
ms.assetid: 350a663e-92ff-44ab-ad53-d94efa2e5823
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b4f702f619eb06a11cbbf7ec5be7407d12f7f445
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368731"
---
# <a name="cdaofieldexchange-class"></a>CDaoFieldExchange 클래스
DAO 데이터베이스 클래스에서 사용하는 DAO 레코드 필드 교환(DFX) 루틴을 지원합니다.  
  
## <a name="syntax"></a>구문  
  
```  
class CDaoFieldExchange  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CDaoFieldExchange::IsValidOperation](#isvalidoperation)|업데이트 되는 필드의 형식에 적합 한 현재 작업 하는 경우 0이 아닌 반환 합니다.|  
|[CDaoFieldExchange::SetFieldType](#setfieldtype)|레코드 집합 데이터 멤버의 유형을 지정-열 또는 매개 변수-다음에 호출할 때까지 모든 후속 DFX 함수 호출을 나타내는 `SetFieldType`합니다.|  
  
### <a name="public-data-members"></a>공용 데이터 멤버  
  
|이름|설명|  
|----------|-----------------|  
|[CDaoFieldExchange::m_nOperation](#m_noperation)|레코드 집합의 현재 호출에서 수행 되는 DFX 작업 `DoFieldExchange` 멤버 함수입니다.|  
|[CDaoFieldExchange::m_prs](#m_prs)|작업은 수행 되는 DFX에서 레코드 집합에 대 한 포인터입니다.|  
  
## <a name="remarks"></a>설명  
 `CDaoFieldExchange` 기본 클래스는 없습니다.  
  
 이 클래스를 사용 하 여 사용자 지정 데이터 형식에 대 한 데이터 교환 루틴을 작성 하는 경우 그렇지 않으면 있습니다 사용 하지 않습니다 직접이 클래스. DFX의 필드 데이터 멤버 간에 데이터를 교환 하면 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 개체와 데이터 소스에서 현재 레코드에서 해당 필드입니다. DFX는 데이터 원본 및 데이터 원본에서 양방향으로 exchange를 관리합니다. 참조 [기술 참고 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) 사용자 지정 DFX 루틴을 작성 하는 방법에 대 한 정보에 대 한 합니다.  
  
> [!NOTE]
>  DAO 데이터베이스 클래스에 ODBC Open Database Connectivity ()를 기반으로 하는 MFC 데이터베이스 클래스와 다릅니다. 모든 DAO 데이터베이스 클래스 이름이 "CDao" 접두사가 있습니다. DAO 클래스의 ODBC 데이터 원본에 액세스할 수 있습니다. 일반적으로 기반으로 DAO MFC 클래스는 ODBC를 기반으로 MFC 클래스 보다 더 수 있습니다. DAO 기반 클래스를 통해 자신의 데이터베이스 엔진을 통해 ODBC 드라이버를 포함 한 데이터를 액세스할 수 있습니다. 또한 사용자가 직접 DAO 호출 하는 대신 클래스를 통해 테이블을 추가 하는 등의 데이터 정의 언어 (DDL) 작업을 지원 합니다.  
  
> [!NOTE]
>  DAO 레코드 필드 교환 (DFX)는 ODBC 기반 MFC 데이터베이스 클래스에서 레코드 필드 교환 (RFX)와 매우 비슷합니다 ( `CDatabase`, `CRecordset`). RFX 이해 하면 사용 하기 쉬운 DFX를 찾이 됩니다.  
  
 A `CDaoFieldExchange` 컨텍스트 정보가 필요한 dao 레코드 필드 교환을 수행 하려면 개체를 제공 합니다. `CDaoFieldExchange` 개체는 현재 레코드의 필드에 다양 한 플래그를 설정 및 매개 변수 및 필드 데이터 멤버를 포함 하 여 작업의 수를 지원 합니다. Dfx에 정의 된 형식의 레코드 집합 클래스 데이터 멤버에 대해 수행 되는 `enum` **FieldType** 에서 `CDaoFieldExchange`합니다. 가능한 **FieldType** 값은:  
  
- **CDaoFieldExchange::outputColumn** 필드 데이터 멤버에 대 한 합니다.  
  
- **CDaoFieldExchange::param** 매개 변수 데이터 멤버에 대 한 합니다.  
  
 [IsValidOperation](#isvalidoperation) 멤버 함수는 사용자 고유의 사용자 지정 DFX 루틴을 작성 하기 위한 제공 됩니다. 사용 하 여 [SetFieldType](#setfieldtype) 에 자주 프로그램 [CDaoRecordset::DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) 함수입니다. DFX 전역 함수에 대 한 세부 정보를 참조 하십시오. [레코드 필드 교환 함수](../../mfc/reference/record-field-exchange-functions.md)합니다. 사용자 지정 데이터 형식에 대 한 사용자 지정 DFX 루틴을 작성 하는 방법에 대 한 정보를 참조 하십시오. [기술 참고 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)합니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 `CDaoFieldExchange`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxdao.h  
  
##  <a name="isvalidoperation"></a>  CDaoFieldExchange::IsValidOperation  
 사용자가 직접 DFX 함수를 작성 하는 경우 호출 `IsValidOperation` 의 특정 필드 데이터 멤버 형식에서 현재 작업을 수행할 수 있는지 여부를 결정 하는 함수 시작 부분에 (한 **CDaoFieldExchange::outputColumn** 또는 **CDaoFieldExchange::param**).  
  
```  
BOOL IsValidOperation();
```  
  
### <a name="return-value"></a>반환 값  
 현재 작업이 업데이트 되는 필드의 형식에 대 한 적절 한 경우에 0이 아닙니다.  
  
### <a name="remarks"></a>설명  
 DFX 메커니즘에 의해 수행 된 작업의 일부 가능한 필드 유형 중 하나에 적용 됩니다. DFX 함수 기존 모델을 따릅니다.  
  
 사용자 지정 DFX 루틴을 작성 방법에 대 한 자세한 내용은 참조 하십시오. [기술 참고 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)합니다.  
  
##  <a name="m_noperation"></a>  CDaoFieldExchange::m_nOperation  
 에 대해 수행할 작업을 식별 하는 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 필드 exchange 개체와 연결 된 개체입니다.  
  
### <a name="remarks"></a>설명  
 `CDaoFieldExchange` 레코드 집합에 대 한 다른 DFX 작업 수에 대 한 컨텍스트를 제공 하는 개체입니다.  
  
> [!NOTE]
>  **PSEUDONULL** MarkForAddNew 및 SetFieldNull 작업 아래에서 설명 하는 값은 Null 필드를 표시 하는 데 사용 하는 값입니다. DAO 레코드 필드 교환 (DFX) 메커니즘 필드 명시적으로 표시 된 Null 확인 하려면이 값을 사용 합니다. **PSEUDONULL** 에 필요 하지 않습니다 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 및 [COleCurrency](../../mfc/reference/colecurrency-class.md) 필드입니다.  
  
 가능한 값 **m_nOperation** 됩니다.  
  
|작업|설명|  
|---------------|-----------------|  
|**AddToParameterList**|빌드는 **매개 변수** SQL 문 절.|  
|**AddToSelectList**|빌드는 **선택** SQL 문 절.|  
|**BindField**|응용 프로그램의 메모리 위치에 데이터베이스의 필드를 바인딩합니다.|  
|**BindParam**|레코드 집합의 쿼리에 대 한 매개 변수 값을 설정합니다.|  
|**픽스업**|필드에 대 한 Null 상태를 설정합니다.|  
|**AllocCache**|레코드 집합의 필드를 "더티"에 대 한 확인 하는 데 사용 되는 캐시를 할당 합니다.|  
|**StoreField**|캐시에 현재 레코드를 저장합니다.|  
|**LoadField**|레코드 집합의 캐시 된 데이터 멤버 변수를 복원합니다.|  
|**FreeCache**|레코드 집합의 필드를 "더티"에 대 한 확인 하는 데 사용 되는 캐시를 해제 합니다.|  
|`SetFieldNull`|필드의 상태 값을 Null로 설정 하는 **PSEUDONULL**합니다.|  
|**MarkForAddNew**|그렇지 않은 경우 필드를 "더티" 표시 **PSEUDONULL**합니다.|  
|**MarkForEdit**|캐시 일치 하지 않는 경우 필드를 "더티" 표시 합니다.|  
|**SetDirtyField**|설정 "변경 합니다."로 표시 된 값 필드|  
|**DumpField**|필드의 내용을 (디버그에만 해당)를 덤프합니다.|  
|**MaxDFXOperation**|입력 검사에 사용 합니다.|  
  
##  <a name="m_prs"></a>  CDaoFieldExchange::m_prs  
 에 대 한 포인터는 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 연관 된 개체는 `CDaoFieldExchange` 개체입니다.  
  
### <a name="remarks"></a>설명  
  
##  <a name="setfieldtype"></a>  CDaoFieldExchange::SetFieldType  
 호출 `SetFieldType` 에 프로그램 `CDaoRecordset` 클래스의 `DoFieldExchange` 재정의 합니다.  
  
```  
void SetFieldType(UINT nFieldType);
```  
  
### <a name="parameters"></a>매개 변수  
 `nFieldType`  
 값은 **enum FieldType**에 선언 된 `CDaoFieldExchange`, 다음 중 하나가 될 수 있는:  
  
- **CDaoFieldExchange::outputColumn**  
  
- **CDaoFieldExchange::param**  
  
### <a name="remarks"></a>설명  
 일반적으로 클래스 마법사는이 호출이를 작성합니다. 사용자 고유의 함수를 작성 하 고 작성 하는 마법사를 사용 하는 경우 프로그램 `DoFieldExchange` 함수, 필드 맵 외부 사용자가 직접 함수 호출을 추가 합니다. 마법사를 사용 하지 않는 경우 되지 않습니다 필드 맵을 합니다. 호출 하거나 클래스의 각 필드 데이터 멤버에 대 한 DFX 함수에 대 한 호출 앞에 오고로 필드 형식을 식별 **CDaoFieldExchange::outputColumn**합니다.  
  
 레코드 집합 클래스를 매개 변수화 필드 map) (외부 모든 매개 변수 데이터 멤버에 대 한 DFX 호출을 추가 하 고 해야을 호출 하 여 이러한 호출 앞에 야 `SetFieldType`합니다. 값을 전달 **CDaoFieldExchange::param**합니다. (대신 사용할 수 있습니다는 [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) 해당 매개 변수 값을 설정 합니다.)  
  
 일반적으로 필드 데이터 멤버 또는 매개 변수 데이터 멤버와 연결 된 DFX 함수 호출의 각 그룹 뒤에 야를 호출 하 여 `SetFieldType`합니다. `nFieldType` 각 매개 변수 `SetFieldType` 호출 다음에 나오는 DFX 함수 호출에 의해 표시 되는 데이터 멤버의 형식을 식별 하는 `SetFieldType` 호출 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [계층 구조 차트](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset 클래스](../../mfc/reference/cdaorecordset-class.md)
