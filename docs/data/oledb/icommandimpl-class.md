---
title: ICommandImpl 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandImpl
dev_langs:
- C++
helpviewer_keywords:
- ICommandImpl class
ms.assetid: ef285fef-0d66-45e6-a762-b03357098e3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d69ff56ec92fd3acb622aa4c0399893fb44c4d1d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="icommandimpl-class"></a>ICommandImpl 클래스
에 대 한 구현을 제공는 [ICommand](https://msdn.microsoft.com/en-us/library/ms709737.aspx) 인터페이스입니다.  
  
## <a name="syntax"></a>구문

```cpp
template <class T, class CommandBase = ICommand>   
class ATL_NO_VTABLE ICommandImpl : public CommandBase  
```  
  
#### <a name="parameters"></a>매개 변수  
 `T`  
 파생 된 클래스에 `ICommandImpl`합니다.  
  
 `CommandBase`  
 인터페이스입니다. 기본값은 `ICommand`입니다.  
  
## <a name="members"></a>멤버  
  
### <a name="methods"></a>메서드  
  
|||  
|-|-|  
|[CancelExecution](../../data/oledb/icommandimpl-cancelexecution.md)|현재 명령 실행을 취소합니다.|  
|[취소](../../data/oledb/icommandimpl-cancel.md)|현재 명령 실행을 취소합니다.|  
|[CreateRowset](../../data/oledb/icommandimpl-createrowset.md)|행 집합 개체를 만듭니다.|  
|[실행](../../data/oledb/icommandimpl-execute.md)|명령을 실행합니다.|  
|[GetDBSession](../../data/oledb/icommandimpl-getdbsession.md)|명령을 만든 세션에 대 한 인터페이스 포인터를 반환 합니다.|  
|[ICommandImpl](../../data/oledb/icommandimpl-icommandimpl.md)|생성자입니다.|  
  
### <a name="data-members"></a>데이터 멤버  
  
|||  
|-|-|  
|[m_bCancel](../../data/oledb/icommandimpl-m-bcancel.md)|명령을 취소할지 여부를 나타냅니다.|  
|[m_bCancelWhenExecuting](../../data/oledb/icommandimpl-m-bcancelwhenexecuting.md)|명령을 실행할 때 취소 여부를 나타냅니다.|  
|[m_bIsExecuting](../../data/oledb/icommandimpl-m-bisexecuting.md)|이 명령은 현재 실행 여부를 나타냅니다.|  
  
## <a name="remarks"></a>설명  
 명령 개체에서 필수 인터페이스입니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atldb.h  
  
## <a name="see-also"></a>참고 항목  
 [OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 공급자 템플릿 구조](../../data/oledb/ole-db-provider-template-architecture.md)