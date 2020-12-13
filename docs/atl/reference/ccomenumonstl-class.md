---
description: '자세히 알아보기: CComEnumOnSTL 클래스'
title: CComEnumOnSTL 클래스
ms.date: 11/04/2016
f1_keywords:
- CComEnumOnSTL
- atlcom/ATL::CComEnumOnSTL
helpviewer_keywords:
- CComEnumOnSTL class
ms.assetid: befe1a44-7a00-4f28-9a2e-cc0fa526643c
ms.openlocfilehash: 1ff73796d7e3eefa76cbecdeb6d997bede2d2be5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146668"
---
# <a name="ccomenumonstl-class"></a>CComEnumOnSTL 클래스

이 클래스는 c + + 표준 라이브러리 컬렉션을 기반으로 COM 열거자 개체를 정의 합니다.

## <a name="syntax"></a>구문

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType, class ThreadModel = CComObjectThreadModel>
class ATL_NO_VTABLE CComEnumOnSTL : public IEnumOnSTLImpl<Base, piid,
T,
    Copy,
CollType>,
    public CComObjectRootEx<ThreadModel>
```

#### <a name="parameters"></a>매개 변수

*하단*<br/>
COM 열거자입니다. 예는 [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) 을 참조 하세요.

*piid*<br/>
열거자 인터페이스의 인터페이스 ID에 대 한 포인터입니다.

*T*<br/>
열거자 인터페이스에 의해 노출 되는 항목의 형식입니다.

*복사*<br/>
[복사 정책](../../atl/atl-copy-policy-classes.md) 클래스입니다.

*CollType*<br/>
C + + 표준 라이브러리 컨테이너 클래스입니다.

## <a name="remarks"></a>설명

`CComEnumOnSTL` c + + 표준 라이브러리 컬렉션을 기반으로 COM 열거자 개체를 정의 합니다. 이 클래스는 자체적으로 사용 하거나 [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)와 함께 사용할 수 있습니다. 이 클래스를 사용 하는 일반적인 단계는 아래에 설명 되어 있습니다. 자세한 내용은 [ATL 컬렉션 및 열거자](../../atl/atl-collections-and-enumerators.md)를 참조 하세요.

## <a name="to-use-this-class-with-icollectiononstlimpl"></a>ICollectionOnSTLImpl와 함께이 클래스를 사용 하려면 다음을 수행 합니다.

- **`typedef`** 이 클래스의 특수화입니다.

- **`typedef`** 의 특수화에서를 최종 템플릿 인수로 사용 합니다 `ICollectionOnSTLImpl` .

예제는 [ATL 컬렉션 및 열거자](../../atl/atl-collections-and-enumerators.md) 를 참조 하세요.

## <a name="to-use-this-class-independently-of-icollectiononstlimpl"></a>ICollectionOnSTLImpl와 독립적으로이 클래스를 사용 하려면

- **`typedef`** 이 클래스의 특수화입니다.

- **`typedef`** 의 특수화에서 템플릿 인수로를 사용 합니다 `CComObject` .

- 특수화의 인스턴스를 만듭니다 `CComObject` .

- [IEnumOnSTLImpl:: Init](../../atl/reference/ienumonstlimpl-class.md#init)를 호출 하 여 열거자 개체를 초기화 합니다.

- 열거자 인터페이스를 클라이언트에 반환 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)

`CComEnumOnSTL`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="example"></a>예제

아래에 표시 된 코드는 열거자 개체의 생성 및 초기화를 처리 하는 제네릭 함수를 제공 합니다.

[!code-cpp[NVC_ATL_COM#34](../../atl/codesnippet/cpp/ccomenumonstl-class_1.h)]

이 템플릿 함수는 `_NewEnum` 아래와 같이 컬렉션 인터페이스의 속성을 구현 하는 데 사용할 수 있습니다.

[!code-cpp[NVC_ATL_COM#35](../../atl/codesnippet/cpp/ccomenumonstl-class_2.h)]

이 코드 **`typedef`** `CComEnumOnSTL` 는 인터페이스를 통해 s의 벡터를 노출 하는에 대 한를 만듭니다 `CComVariant` `IEnumVariant` . `CVariantCollection`클래스는 `CreateSTLEnumerator` 이 형식의 열거자 개체를 사용 하는 작업을 간단 하 게 합니다.

## <a name="see-also"></a>참고 항목

[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)<br/>
[ICollectionOnSTLImpl 컬렉션 샘플:, CComEnumOnSTL 및 사용자 지정 복사 정책 클래스를 보여 줍니다.](../../overview/visual-cpp-samples.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)<br/>
[CComObjectRootEx 클래스](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[IEnumOnSTLImpl 클래스](../../atl/reference/ienumonstlimpl-class.md)
