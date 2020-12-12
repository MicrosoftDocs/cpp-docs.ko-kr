---
description: '자세한 정보: CAtlAutoThreadModule 클래스'
title: CAtlAutoThreadModule 클래스
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModule
- atlbase/ATL::CAtlAutoThreadModule
helpviewer_keywords:
- CAtlAutoThreadModule class
ms.assetid: 3be834aa-55ef-403e-94ae-41979691b15f
ms.openlocfilehash: d1742488cca84dccfa53753bec40f9081d77f67d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165058"
---
# <a name="catlautothreadmodule-class"></a>CAtlAutoThreadModule 클래스

이 클래스는 스레드 풀의 아파트 모델 COM 서버를 구현 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
class CAtlAutoThreadModule : public CAtlAutoThreadModuleT<CAtlAutoThreadModule>
```

## <a name="remarks"></a>설명

`CAtlAutoThreadModule` 은 (는) [Catlautothreadmodulet](../../atl/reference/catlautothreadmodulet-class.md) 에서 파생 되며 스레드 풀의 아파트 모델 COM 서버를 구현 합니다. `CAtlAutoThreadModule`[CComApartment](../../atl/reference/ccomapartment-class.md) 를 사용 하 여 모듈의 각 스레드에 대 한 아파트를 관리 합니다.

[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) 을 클래스 팩터리로 지정 하려면 개체의 클래스 정의에 [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) 매크로를 사용 해야 합니다. 그런 다음와 같은에서 파생 된 클래스의 단일 인스턴스를 추가 해야 합니다 `CAtlAutoThreadModuleT` `CAtlAutoThreadModule` . 예를 들어:

`CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`

> [!NOTE]
> 이 클래스는 사용 되지 않는 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) 클래스를 대체 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IAtlAutoThreadModule`

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

`CAtlAutoThreadModule`

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="see-also"></a>참고 항목

[CAtlAutoThreadModuleT 클래스](../../atl/reference/catlautothreadmodulet-class.md)<br/>
[IAtlAutoThreadModule 클래스](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)<br/>
[모듈 클래스](../../atl/atl-module-classes.md)
