---
description: '자세한 정보: 예외 처리 매크로'
title: 예외 처리 매크로
ms.date: 11/04/2016
f1_keywords:
- atldef/ATL::_ATLCATCH
- atldef/ATL::_ATLCATCHALL
- atldef/ATL::_ATLTRY
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
ms.openlocfilehash: 8d5e6564dec5769fb172c66b3102677e58cbd788
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139830"
---
# <a name="exception-handling-macros"></a>예외 처리 매크로

이러한 매크로는 예외 처리에 대 한 지원을 제공 합니다.

|Name|설명|
|-|-|
|[_ATLCATCH](#_atlcatch)|연결 된에서 발생 하는 오류를 처리 하는 문입니다 `_ATLTRY` .|
|[_ATLCATCHALL](#_atlcatchall)|연결 된에서 발생 하는 오류를 처리 하는 문입니다 `_ATLTRY` .|
|[_ATLTRY](#_atltry)|오류가 발생할 수 있는 보호 된 코드 섹션을 표시 합니다.|

## <a name="requirements"></a>요구 사항:

**헤더:**

## <a name="_atlcatch"></a><a name="_atlcatch"></a> _ATLCATCH

연결 된에서 발생 하는 오류를 처리 하는 문입니다 `_ATLTRY` .

```
_ATLCATCH(e)
```

### <a name="parameters"></a>매개 변수

*e*<br/>
Catch 할 예외입니다.

### <a name="remarks"></a>설명

과 함께 사용 `_ATLTRY` 됩니다. 지정 된 형식의 c + + 예외를 처리 하는 c + + [catch (CAtlException e)](../../cpp/try-throw-and-catch-statements-cpp.md) 를 확인 합니다.

## <a name="_atlcatchall"></a><a name="_atlcatchall"></a> _ATLCATCHALL

연결 된에서 발생 하는 오류를 처리 하는 문입니다 `_ATLTRY` .

```
_ATLCATCHALL
```

### <a name="remarks"></a>설명

과 함께 사용 `_ATLTRY` 됩니다. 모든 형식의 c + + 예외를 처리 하기 위한 c + + [catch (...)](../../cpp/try-throw-and-catch-statements-cpp.md) 로 확인 됩니다.

## <a name="_atltry"></a><a name="_atltry"></a> _ATLTRY

오류가 발생할 수 있는 보호 된 코드 섹션을 표시 합니다.

```
_ATLTRY
```

### <a name="remarks"></a>설명

[_ATLCATCH](#_atlcatch) 또는 [_ATLCATCHALL](#_atlcatchall)와 함께 사용 됩니다. C + + 기호 [시도](../../cpp/try-throw-and-catch-statements-cpp.md)로 확인 됩니다.

## <a name="see-also"></a>참고 항목

[매크로](../../atl/reference/atl-macros.md)
