---
description: '자세히 알아보기: IPropertyNotifySinkCP 클래스'
title: IPropertyNotifySinkCP 클래스
ms.date: 11/04/2016
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
ms.openlocfilehash: 096a24a22634be23c7ede955c7ae49c3dd963f66
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158363"
---
# <a name="ipropertynotifysinkcp-class"></a>IPropertyNotifySinkCP 클래스

이 클래스는 연결 가능한 개체의 나가는 인터페이스로 [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) interface를 노출 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template<class T, class CDV = CComDynamicUnkArray>
class IPropertyNotifySinkCP
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IPropertyNotifySinkCP` 입니다.

*CDV*<br/>
연결 지점과 해당 싱크 간의 연결을 관리 하는 클래스입니다. 기본값은 무제한 연결을 허용 하는 [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)입니다. 고정 된 수의 연결을 지정 하는 [CComUnkArray](../../atl/reference/ccomunkarray-class.md)를 사용할 수도 있습니다.

## <a name="remarks"></a>설명

`IPropertyNotifySinkCP` 기본 클래스 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)를 통해 모든 메서드를 상속 합니다.

[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) 인터페이스를 사용 하면 싱크 개체가 속성 변경에 대 한 알림을 받을 수 있습니다. 클래스 `IPropertyNotifySinkCP` 는 연결 가능한 개체에서이 인터페이스를 나가는 인터페이스로 노출 합니다. 클라이언트는 싱크에 대해 메서드를 구현 해야 합니다 `IPropertyNotifySink` .

`IPropertyNotifySinkCP`인터페이스를 나타내는 연결점을 만들려는 경우에서 클래스를 파생 시킵니다 `IPropertyNotifySink` .

ATL에서 연결 지점의 사용에 대 한 자세한 내용은 [연결 요소](../../atl/atl-connection-points.md)문서를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** 없음 ctl. h

## <a name="see-also"></a>참고 항목

[IConnectionPointImpl 클래스](../../atl/reference/iconnectionpointimpl-class.md)<br/>
[IConnectionPointContainerImpl 클래스](../../atl/reference/iconnectionpointcontainerimpl-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
