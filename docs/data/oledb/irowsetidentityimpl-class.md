---
title: IRowsetIdentityImpl 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetIdentityImpl
- ATL.IRowsetIdentityImpl
- IRowsetIdentityImpl
- IsSameRow
- IRowsetIdentityImpl.IsSameRow
- ATL.IRowsetIdentityImpl.IsSameRow
- IRowsetIdentityImpl::IsSameRow
- ATL::IRowsetIdentityImpl::IsSameRow
dev_langs:
- C++
helpviewer_keywords:
- IRowsetIdentityImpl class
- IsSameRow method
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1431fb9b35ab83f6cb0fc167eff4ba4508f2e301
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036191"
---
# <a name="irowsetidentityimpl-class"></a>IRowsetIdentityImpl 클래스

OLE DB 구현 [IRowsetIdentity](/previous-versions/windows/desktop/ms715913\(v=vs.85\)) 행 id에 대 한 테스트 수 있도록 하는 인터페이스입니다.  
  
## <a name="syntax"></a>구문

```cpp
template <class T, class RowClass = CSimpleRow>  
class ATL_NO_VTABLE IRowsetIdentityImpl   
   : public IRowsetIdentity  
```  
  
### <a name="parameters"></a>매개 변수  

*T*<br/>
파생 된 클래스 `IRowsetIdentityImpl`합니다.  
  
*RowClass*<br/>
에 대 한 저장소 단위는 `HROW`합니다.  

## <a name="requirements"></a>요구 사항  

**헤더:** atldb.h  
  
## <a name="members"></a>멤버  
  
### <a name="methods"></a>메서드  
  
|||  
|-|-|  
|[IsSameRow](#issamerow)|동일한 행을 참조 하는 경우를 확인 하려면 두 개의 행 핸들을 비교 합니다.|  
  
## <a name="issamerow"></a> Irowsetidentityimpl:: Issamerow

동일한 행을 참조 하는 경우를 확인 하려면 두 개의 행 핸들을 비교 합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp
STDMETHOD(IsSameRow )(HROW hThisRow,  
   HROW hThatRow);  
```  
  
#### <a name="parameters"></a>매개 변수  

참조 [IRowsetIdentity::IsSameRow](/previous-versions/windows/desktop/ms719629\(v=vs.85\)) 에 *OLE DB Programmer's Reference*합니다.  
  
### <a name="remarks"></a>설명  

행 핸들을 비교 하려면이 메서드는 다음과 같이 캐스팅 됩니다.는 `HROW` 핸들 `RowClass` 멤버 및 호출 `memcmp` 는 포인터에 대 한 합니다.  
  
## <a name="see-also"></a>참고 항목  

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 구조](../../data/oledb/ole-db-provider-template-architecture.md)