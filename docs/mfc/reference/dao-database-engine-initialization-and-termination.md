---
description: '자세한 정보: DAO 데이터베이스 엔진 초기화 및 종료'
title: DAO 데이터베이스 엔진 초기화 및 종료
ms.date: 09/17/2019
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 9e9b522d744eabc84074b201051151b80ed75d7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220398"
---
# <a name="dao-database-engine-initialization-and-termination"></a>DAO 데이터베이스 엔진 초기화 및 종료

DAO는 Access 데이터베이스에 사용 되며 Office 2013을 통해 지원 됩니다. DAO 3.6은 최종 버전이 며 사용 되지 않는 것으로 간주 됩니다. MFC DAO 개체를 사용 하는 경우 응용 프로그램 또는 DLL이 종료 되기 전에 먼저 DAO 데이터베이스 엔진을 초기화 하 고 종료 해야 합니다. 및의 두 함수는 `AfxDaoInit` `AfxDaoTerm` 이러한 작업을 수행 합니다.

### <a name="dao-database-engine-initialization-and-termination"></a>DAO 데이터베이스 엔진 초기화 및 종료

|Name|설명|
|-|-|
|[AfxDaoInit](#afxdaoinit)|DAO 데이터베이스 엔진을 초기화 합니다.|
|[AfxDaoTerm](#afxdaoterm)|DAO 데이터베이스 엔진을 종료 합니다.|

## <a name="afxdaoinit"></a><a name="afxdaoinit"></a> AfxDaoInit

이 함수는 DAO 데이터베이스 엔진을 초기화 합니다.

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>설명

대부분의 경우 `AfxDaoInit` 필요할 때 응용 프로그램에서 자동으로 호출 하므로를 호출할 필요가 없습니다.

관련 정보 및를 호출 하는 예제는 `AfxDaoInit` [기술 참고 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)를 참조 하십시오.

### <a name="requirements"></a>요구 사항

  **헤더** afxdao

## <a name="afxdaoterm"></a><a name="afxdaoterm"></a> AfxDaoTerm

이 함수는 DAO 데이터베이스 엔진을 종료 합니다.

```

void AfxDaoTerm();
```

### <a name="remarks"></a>설명

일반적으로 일반 MFC DLL 에서만이 함수를 호출 해야 합니다. 응용 프로그램은 필요할 때 자동으로를 호출 `AfxDaoTerm` 합니다.

일반 MFC Dll에서 함수 전에를 호출 하 고, `AfxDaoTerm` `ExitInstance` 모든 MFC DAO 개체가 제거 된 후에를 호출 합니다.

관련 정보는 [기술 참고 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)을 참조 하세요.

### <a name="requirements"></a>요구 사항

  **헤더** afxdao

## <a name="see-also"></a>참고 항목

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)
