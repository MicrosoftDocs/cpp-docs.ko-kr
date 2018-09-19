---
title: DAO 데이터베이스 엔진 초기화 및 종료 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.data
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8cf54992896559f1b143247746ef9f9e0e8d8979
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404009"
---
# <a name="dao-database-engine-initialization-and-termination"></a>DAO 데이터베이스 엔진 초기화 및 종료

먼저 DAO 데이터베이스 엔진 해야 MFC DAO 개체를 사용 하는 경우 초기화 및 종료 한 다음 응용 프로그램 또는 DLL 종료 되기 전에 합니다. 두 개의 함수가 `AfxDaoInit` 및 `AfxDaoTerm`, 이러한 작업을 수행 합니다.

### <a name="dao-database-engine-initialization-and-termination"></a>DAO 데이터베이스 엔진 초기화 및 종료

|||
|-|-|
|[AfxDaoInit](#afxdaoinit)|DAO 데이터베이스 엔진을 초기화합니다.|
|[AfxDaoTerm](#afxdaoterm)|DAO 데이터베이스 엔진을 종료합니다.|

##  <a name="afxdaoinit"></a>  AfxDaoInit

이 함수는 DAO 데이터베이스 엔진을 초기화합니다.

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>설명

대부분의 경우에서 호출할 필요가 `AfxDaoInit` 응용 프로그램이 자동으로 호출 하므로 필요할 때.

관련 정보 및 호출 하는 예제 `AfxDaoInit`를 참조 하세요 [기술 참고 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdao.h

##  <a name="afxdaoterm"></a>  AfxDaoTerm

이 함수는 DAO 데이터베이스 엔진을 종료합니다.

```

void AfxDaoTerm();
```

### <a name="remarks"></a>설명

일반 MFC DLL;에서이 함수를 호출 하려면만 하면 일반적으로 응용 프로그램에서는 자동으로 호출 `AfxDaoTerm` 필요할 때.

기본 MFC Dll에서 호출 `AfxDaoTerm` 하기 전에 `ExitInstance` 함수 되지만 MFC DAO 개체를 모두 제거 된 후입니다.

관련 정보를 참조 하세요 [기술 참고 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxdao.h

## <a name="see-also"></a>참고 항목

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)
