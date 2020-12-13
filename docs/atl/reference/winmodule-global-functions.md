---
description: '자세히 알아보기: WinModule 전역 함수'
title: WinModule 전역 함수
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
ms.openlocfilehash: 1ea232bd3db79f3be3d9dee32b5f9fa40df0eb79
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138660"
---
# <a name="winmodule-global-functions"></a>WinModule 전역 함수

이러한 함수는 구조 작업에 대 한 지원을 제공 `_AtlCreateWndData` 합니다.

> [!IMPORTANT]
> 다음 표에 나열 된 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

|Name|설명|
|-|-|
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|이 함수는 `_AtlCreateWndData` 구조를 초기화하고 추가하는 데 사용됩니다.|
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|기존 `_AtlCreateWndData` 구조를 추출하려면 이 함수를 호출합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="atlwinmoduleaddcreatewnddata"></a><a name="atlwinmoduleaddcreatewnddata"></a> AtlWinModuleAddCreateWndData

이 함수는 `_AtlCreateWndData` 구조를 초기화하고 추가하는 데 사용됩니다.

```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```

### <a name="parameters"></a>매개 변수

*pWinModule*<br/>
모듈의 [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) 구조에 대 한 포인터입니다.

*pData*<br/>
초기화 되어 현재 모듈에 추가 되는 [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) 구조체에 대 한 포인터입니다.

*pObject*<br/>
개체의 포인터에 대 한 포인터 **`this`** 입니다.

### <a name="remarks"></a>설명

`_AtlCreateWndData` **`this`** 클래스 인스턴스를 참조 하는 데 사용 되는 포인터를 저장 하 고 모듈의 구조에서 참조 되는 목록에 추가 하는 데 사용 되는 구조체를 초기화 `_ATL_WIN_MODULE70` 합니다. [Catlwinmodule:: AddCreateWndData](catlwinmodule-class.md#addcreatewnddata)에서 호출 됩니다.

## <a name="atlwinmoduleextractcreatewnddata"></a><a name="atlwinmoduleextractcreatewnddata"></a> AtlWinModuleExtractCreateWndData

기존 `_AtlCreateWndData` 구조를 추출하려면 이 함수를 호출합니다.

```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```

### <a name="parameters"></a>매개 변수

*pWinModule*<br/>
모듈의 [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) 구조에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) 구조체에 대 한 포인터를 반환 합니다.

### <a name="remarks"></a>설명

이 함수는 `_AtlCreateWndData` 모듈의 구조에서 참조 하는 목록에서 기존 구조체를 추출 `_ATL_WIN_MODULE70` 합니다.

## <a name="see-also"></a>참조

[함수](../../atl/reference/atl-functions.md)
