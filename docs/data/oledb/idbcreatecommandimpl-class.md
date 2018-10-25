---
title: IDBCreateCommandImpl 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
- IDBCreateCommandImpl.CreateCommand
- CreateCommand
- IDBCreateCommandImpl::CreateCommand
dev_langs:
- C++
helpviewer_keywords:
- IDBCreateCommandImpl class
- CreateCommand method
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 727d50025ce7fc4808444ac7ad73d828c6f0c545
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053517"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl 클래스

구현을 제공 합니다 [IDBCreateCommand](/previous-versions/windows/desktop/ms711625) 인터페이스입니다.

## <a name="syntax"></a>구문

```cpp
template <class T, class CommandClass >
class ATL_NO_VTABLE IDBCreateCommandImpl
   : public IDBCreateCommand
```

### <a name="parameters"></a>매개 변수

*T*<br/>
세션 개체에서 파생 된 `IDBCreateCommandImpl`합니다.

*CommandClass*<br/>
명령 클래스입니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldb.h

## <a name="members"></a>멤버

### <a name="interface-methods"></a>인터페이스 메서드

|||
|-|-|
|[CreateCommand](#createcommand)|새 명령을 만듭니다.|

## <a name="remarks"></a>설명

새 명령을 가져올 세션 개체의 선택적 인터페이스입니다.

## <a name="createcommand"></a> Idbcreatecommandimpl:: Createcommand

새 명령을 만들고 요청된 된 인터페이스를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(CreateCommand)(IUnknown * pUnkOuter, 
   REFIID riid, 
   IUnknown ** ppvCommand);
```

#### <a name="parameters"></a>매개 변수

참조 [idbcreatecommand:: Createcommand](/previous-versions/windows/desktop/ms709772) 에 *OLE DB Programmer's Reference*합니다.

에 해당 하는 일부 매개 변수 *OLE DB Programmer's Reference* 매개 변수에서 설명 하는 다른 이름의 `IDBCreateCommand::CreateCommand`:

|OLE DB 템플릿 매개 변수|*OLE DB Programmer's Reference* 매개 변수|
|--------------------------------|------------------------------------------------|
|*ppvCommand*|*ppCommand*|

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 구조](../../data/oledb/ole-db-provider-template-architecture.md)