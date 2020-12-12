---
description: '자세히 알아보기: CComEnum 클래스'
title: CComEnum 클래스
ms.date: 11/04/2016
f1_keywords:
- CComEnum
- atlcom/ATL::CComEnum
helpviewer_keywords:
- CComEnum class
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
ms.openlocfilehash: 0cee4129c0bc5129313b92e144c22de9d161c9cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146694"
---
# <a name="ccomenum-class"></a>CComEnum 클래스

이 클래스는 배열을 기반으로 COM 열거자 개체를 정의 합니다.

## <a name="syntax"></a>구문

```
template <class Base,
    const IID* piid, class T, class Copy, class ThreadModel = CcomObjectThreadModel>
class ATL_NO_VTABLE CComEnum : public CComEnumImpl<Base, piid,
T,
    Copy>,
public CComObjectRootEx<ThreadModel>
```

#### <a name="parameters"></a>매개 변수

*하단*<br/>
COM 열거자 인터페이스입니다. 예는 [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) 을 참조 하세요.

*piid*<br/>
열거자 인터페이스의 인터페이스 ID에 대 한 포인터입니다.

*T*<br/>
열거자 인터페이스에 의해 노출 되는 항목의 형식입니다.

*복사*<br/>
유형이 같은 [복사 정책 클래스](../../atl/atl-copy-policy-classes.md)입니다.

*ThreadModel*<br/>
클래스의 스레딩 모델입니다. 이 매개 변수는 기본적으로 프로젝트에 사용 되는 전역 개체 스레드 모델로 사용 됩니다.

## <a name="remarks"></a>설명

`CComEnum` 배열을 기반으로 COM 열거자 개체를 정의 합니다. 이 클래스는 c + + 표준 라이브러리 컨테이너를 기반으로 열거자를 구현 하는 [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md) 와 유사 합니다. 이 클래스를 사용 하는 일반적인 단계는 아래에 설명 되어 있습니다. 자세한 내용은 [ATL 컬렉션 및 열거자](../../atl/atl-collections-and-enumerators.md)를 참조 하세요.

## <a name="to-use-this-class"></a>이 클래스를 사용 하려면 다음을 수행 합니다.

- **`typedef`** 이 클래스의 특수화입니다.

- **`typedef`** 의 특수화에서 템플릿 인수로를 사용 합니다 `CComObject` .

- 특수화의 인스턴스를 만듭니다 `CComObject` .

- [CComEnumImpl:: Init](../../atl/reference/ccomenumimpl-class.md#init)를 호출 하 여 열거자 개체를 초기화 합니다.

- 열거자 인터페이스를 클라이언트에 반환 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)

`CComEnum`

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="example"></a>예제

아래에 표시 된 코드는 열거자 개체를 만들고 초기화 하는 데 사용할 수 있는 기능을 제공 합니다.

[!code-cpp[NVC_ATL_COM#32](../../atl/codesnippet/cpp/ccomenum-class_1.h)]

이 템플릿 함수는 `_NewEnum` 아래와 같이 컬렉션 인터페이스의 속성을 구현 하는 데 사용할 수 있습니다.

[!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/cpp/ccomenum-class_2.h)]

이 코드 **`typedef`** `CComEnum` 는 인터페이스를 통해 변형 벡터를 노출 하는에 대 한를 만듭니다 `IEnumVariant` . `CVariantArrayCollection`클래스는 `CreateEnumerator` 이 형식의 열거자 개체를 사용 하 여 작업 하 고 필요한 인수를 전달 하는 작업을 간단 하 게 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[CComEnumImpl 클래스](../../atl/reference/ccomenumimpl-class.md)<br/>
[CComObjectRootEx 클래스](../../atl/reference/ccomobjectrootex-class.md)
