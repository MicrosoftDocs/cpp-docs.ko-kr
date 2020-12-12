---
description: '자세히 알아보기: 형식 라이브러리 액세스'
title: 형식 라이브러리 액세스
ms.date: 11/04/2016
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
ms.openlocfilehash: c855f82914e540ab13f4bc20581c041633b5bc0d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218656"
---
# <a name="type-library-access"></a>형식 라이브러리 액세스

형식 라이브러리는 OLE 컨트롤의 인터페이스를 다른 OLE 인식 응용 프로그램에 노출 합니다. 하나 이상의 인터페이스를 노출 하려면 각 OLE 컨트롤에 형식 라이브러리가 있어야 합니다.

다음 매크로를 사용 하 여 OLE 컨트롤에서 자체 형식 라이브러리에 대 한 액세스를 제공할 수 있습니다.

### <a name="type-library-access"></a>형식 라이브러리 액세스

|Name|설명|
|-|-|
|[DECLARE_OLETYPELIB](#declare_oletypelib)|`GetTypeLib`OLE 컨트롤의 멤버 함수를 선언 합니다 .이 함수는 클래스 선언에서 사용 되어야 합니다.|
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|`GetTypeLib`OLE 컨트롤의 멤버 함수를 구현 합니다 (클래스 구현에서 사용 되어야 함).|

## <a name="declare_oletypelib"></a><a name="declare_oletypelib"></a> DECLARE_OLETYPELIB

`GetTypeLib`컨트롤 클래스의 멤버 함수를 선언 합니다.

```
DECLARE_OLETYPELIB(class_name)
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
형식 라이브러리와 관련 된 컨트롤 클래스의 이름입니다.

### <a name="remarks"></a>설명

컨트롤 클래스 헤더 파일에서이 매크로를 사용 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="implement_oletypelib"></a><a name="implement_oletypelib"></a> IMPLEMENT_OLETYPELIB

컨트롤의 `GetTypeLib` 멤버 함수를 구현 합니다.

```
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
형식 라이브러리와 관련 된 컨트롤 클래스의 이름입니다.

*tlid*<br/>
형식 라이브러리의 ID 번호입니다.

*wVerMajor*<br/>
형식 라이브러리의 주 버전 번호입니다.

*wVerMinor*<br/>
형식 라이브러리의 부 버전 번호입니다.

### <a name="remarks"></a>설명

이 매크로는 DECLARE_OLETYPELIB 매크로를 사용 하는 모든 컨트롤 클래스의 구현 파일에 표시 되어야 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="see-also"></a>참고 항목

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)
