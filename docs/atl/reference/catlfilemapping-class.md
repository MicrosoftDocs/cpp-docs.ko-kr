---
description: '자세히 알아보기: CAtlFileMapping 클래스'
title: CAtlFileMapping 클래스
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
ms.openlocfilehash: 875979d47ad4cb5b9c59047eff1f50acd35d1251
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147422"
---
# <a name="catlfilemapping-class"></a>CAtlFileMapping 클래스

이 클래스는 [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)의 메서드에 캐스트 연산자를 추가 하 여 메모리 매핑된 파일을 나타냅니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template <typename T = char>
class CAtlFileMapping : public CAtlFileMappingBase
```

### <a name="parameters"></a>매개 변수

*T*<br/>
Cast 연산자에 사용 되는 데이터 형식입니다.

## <a name="members"></a>멤버

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CAtlFileMapping:: operator T *](#operator_t_star)|`CAtlFileMapping`개체를로 암시적으로 변환할 수 있습니다 `T*` .|

## <a name="remarks"></a>설명

이 클래스는 개체를로 암시적으로 변환할 수 있도록 단일 캐스트 연산자를 추가 `CAtlFileMapping` `T*` 합니다. 다른 멤버는 기본 클래스인 [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)에서 제공 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>요구 사항

**헤더:** 이 파일 .h

## <a name="catlfilemappingoperator-t"></a><a name="operator_t_star"></a> CAtlFileMapping:: operator T *

`CAtlFileMapping`개체를로 암시적으로 변환할 수 있습니다 `T*` .

```cpp
operator T*() const throw();
```

### <a name="return-value"></a>반환 값

`T*`메모리 매핑된 파일의 시작에 대 한 포인터를 반환 합니다.

### <a name="remarks"></a>설명

[CAtlFileMappingBase:: GetData](../../atl/reference/catlfilemappingbase-class.md#getdata) 를 호출 하 고 반환 된 포인터를로 다시 해석 합니다 `T*` . 여기서 *T* 는이 클래스의 템플릿 매개 변수로 사용 되는 형식입니다.

## <a name="see-also"></a>참고 항목

[CAtlFileMappingBase 클래스](../../atl/reference/catlfilemappingbase-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
