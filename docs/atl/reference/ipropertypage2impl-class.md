---
title: IPropertyPage2Impl 클래스
ms.date: 11/04/2016
f1_keywords:
- IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl::EditProperty
helpviewer_keywords:
- property pages
- IPropertyPage2 ATL implementation
- IPropertyPage2Impl class
ms.assetid: e89fbe90-203a-47f0-a5de-23616697e1ce
ms.openlocfilehash: 5ec6cb2f4fc6931a1bec429068b558bf7ac1906e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495602"
---
# <a name="ipropertypage2impl-class"></a>IPropertyPage2Impl 클래스

이 클래스는 `IUnknown` [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)의 기본 구현을 구현 하 고 상속 합니다.

> [!IMPORTANT]
>  이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template<class T>
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
에서 `IPropertyPage2Impl`파생 된 클래스입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|Description|
|----------|-----------------|
|[IPropertyPage2Impl::EditProperty](#editproperty)|속성 페이지가 활성화 될 때 포커스를 받을 속성 컨트롤을 지정 합니다. ATL 구현은 E_NOTIMPL을 반환 합니다.|

## <a name="remarks"></a>설명

[IPropertyPage2](/windows/win32/api/ocidl/nn-ocidl-ipropertypage2) 인터페이스는 `EditProperty` 메서드를 추가하여 [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage)를 확장합니다. 이 메서드를 사용 하면 클라이언트에서 속성 페이지 개체의 특정 속성을 선택할 수 있습니다.

클래스 `IPropertyPage2Impl` 는 단순히에 대해 `IPropertyPage2::EditProperty`E_NOTIMPL을 반환 합니다. 그러나이 메서드는 [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md) 의 기본 구현을 상속 하 고 `IUnknown` 디버그 빌드에서 정보를 덤프 장치로 전송 하 여를 구현 합니다.

속성 페이지를 만들 때 클래스는 일반적으로에서 `IPropertyPageImpl`파생 됩니다. 에 대 `IPropertyPage2`한 추가 지원을 제공 하려면 클래스 정의를 수정 하 고 `EditProperty` 메서드를 재정의 합니다.

**관련 문서** Atl [자습서](../../atl/active-template-library-atl-tutorial.md), [atl 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IPropertyPage`

[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)

`IPropertyPage2Impl`

## <a name="requirements"></a>요구 사항

**헤더:** 없음 ctl. h

##  <a name="editproperty"></a>  IPropertyPage2Impl::EditProperty

속성 페이지가 활성화 될 때 포커스를 받을 속성 컨트롤을 지정 합니다.

```
HRESULT EditProperty(DISPID dispID);
```

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환 합니다.

### <a name="remarks"></a>설명

Windows SDK [IPropertyPage2:: EditProperty](/windows/win32/api/ocidl/nf-ocidl-ipropertypage2-editproperty) 를 참조 하세요.

## <a name="see-also"></a>참고자료

[IPerPropertyBrowsingImpl 클래스](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl 클래스](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
