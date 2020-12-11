---
description: '자세한 정보: 집계 및 클래스 팩터리 매크로'
title: 집계 및 클래스 팩터리 매크로
ms.date: 08/12/2020
f1_keywords:
- ATLCOM/ATL::DECLARE_AGGREGATABLE
- ATLCOM/ATL::DECLARE_CLASSFACTORY
- ATLCOM/ATL::DECLARE_CLASSFACTORY_EX
- ATLCOM/ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- ATLCOM/ATL::DECLARE_CLASSFACTORY_SINGLETON
- ATLCOM/ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- ATLCOM/ATL::DECLARE_NOT_AGGREGATABLE
- ATLCOM/ATL::DECLARE_ONLY_AGGREGATABLE
- ATLCOM/ATL::DECLARE_POLY_AGGREGATABLE
- ATLCOM/ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- ATLCOM/ATL::DECLARE_VIEW_STATUS
- ATLDEF/ATL::DECLARE_AGGREGATABLE
- ATLDEF/ATL::DECLARE_CLASSFACTORY
- ATLDEF/ATL::DECLARE_CLASSFACTORY_EX
- ATLDEF/ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- ATLDEF/ATL::DECLARE_CLASSFACTORY_SINGLETON
- ATLDEF/ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- ATLDEF/ATL::DECLARE_NOT_AGGREGATABLE
- ATLDEF/ATL::DECLARE_ONLY_AGGREGATABLE
- ATLDEF/ATL::DECLARE_POLY_AGGREGATABLE
- ATLDEF/ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- ATLDEF/ATL::DECLARE_VIEW_STATUS
- ATLCOM/DECLARE_AGGREGATABLE
- ATLCOM/DECLARE_CLASSFACTORY
- ATLCOM/DECLARE_CLASSFACTORY_EX
- ATLCOM/DECLARE_CLASSFACTORY_AUTO_THREAD
- ATLCOM/DECLARE_CLASSFACTORY_SINGLETON
- ATLCOM/DECLARE_GET_CONTROLLING_UNKNOWN
- ATLCOM/DECLARE_NOT_AGGREGATABLE
- ATLCOM/DECLARE_ONLY_AGGREGATABLE
- ATLCOM/DECLARE_POLY_AGGREGATABLE
- ATLCOM/DECLARE_PROTECT_FINAL_CONSTRUCT
- ATLCOM/DECLARE_VIEW_STATUS
- ATL::DECLARE_AGGREGATABLE
- ATL::DECLARE_CLASSFACTORY
- ATL::DECLARE_CLASSFACTORY_EX
- ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- ATL::DECLARE_CLASSFACTORY_SINGLETON
- ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- ATL::DECLARE_NOT_AGGREGATABLE
- ATL::DECLARE_ONLY_AGGREGATABLE
- ATL::DECLARE_POLY_AGGREGATABLE
- ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- ATL::DECLARE_VIEW_STATUS
- DECLARE_AGGREGATABLE
- DECLARE_CLASSFACTORY
- DECLARE_CLASSFACTORY_EX
- DECLARE_CLASSFACTORY_AUTO_THREAD
- DECLARE_CLASSFACTORY_SINGLETON
- DECLARE_GET_CONTROLLING_UNKNOWN
- DECLARE_NOT_AGGREGATABLE
- DECLARE_ONLY_AGGREGATABLE
- DECLARE_POLY_AGGREGATABLE
- DECLARE_PROTECT_FINAL_CONSTRUCT
- DECLARE_VIEW_STATUS
helpviewer_keywords:
- class factories, ATL macros
- aggregation [C++], ATL macros
- ATL::DECLARE_AGGREGATABLE
- ATL::DECLARE_CLASSFACTORY
- ATL::DECLARE_CLASSFACTORY_EX
- ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- ATL::DECLARE_CLASSFACTORY_SINGLETON
- ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- ATL::DECLARE_NOT_AGGREGATABLE
- ATL::DECLARE_ONLY_AGGREGATABLE
- ATL::DECLARE_POLY_AGGREGATABLE
- ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- ATL::DECLARE_VIEW_STATUS
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
ms.openlocfilehash: 7aa62bfe8e87b9e7923dfe1de1f28b6acdba595e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158961"
---
# <a name="aggregation-and-class-factory-macros"></a>집계 및 클래스 팩터리 매크로

이러한 매크로는 집계를 제어 하 고 클래스 팩터리를 선언 하는 방법을 제공 합니다.

| 매크로 | 설명 |
|--|--|
| [DECLARE_AGGREGATABLE](#declare_aggregatable) | 개체를 집계할 수 있음을 선언 합니다 (기본값). |
| [DECLARE_CLASSFACTORY](#declare_classfactory) | 클래스 팩터리를 ATL 기본 클래스 팩터리로 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)선언 합니다. |
| [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex) | 클래스 팩터리 개체를 클래스 팩터리로 선언 합니다. |
| [DECLARE_CLASSFACTORY2](#declare_classfactory2) | [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) 을 클래스 팩터리로 선언 합니다. |
| [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) | [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) 을 클래스 팩터리로 선언 합니다. |
| [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) | [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) 을 클래스 팩터리로 선언 합니다. |
| [DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown) | 가상 함수를 선언 `GetControllingUnknown` 합니다. |
| [DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) | 개체를 집계할 수 없음을 선언 합니다. |
| [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) | 개체를 집계 해야 함을 선언 합니다. |
| [DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable) | 외부에서 알 수 없는 값을 확인 하 고 적절 하 게 집계할 수 있는 개체 또는 집계할 수 없는 개체를 선언 합니다. |
| [DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct) | 내부 개체를 생성 하는 동안 외부 개체가 삭제 되지 않도록 보호 합니다. |
| [DECLARE_VIEW_STATUS](#declare_view_status) | 컨테이너에 VIEWSTATUS 플래그를 지정 합니다. |

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="declare_aggregatable"></a><a name="declare_aggregatable"></a> DECLARE_AGGREGATABLE

개체를 집계할 수 있도록 지정 합니다.

```cpp
DECLARE_AGGREGATABLE( x )
```

### <a name="parameters"></a>매개 변수

*x*<br/>
진행 집계할 수 있는 것으로 정의 하는 클래스의 이름입니다.

### <a name="remarks"></a>설명

[CComCoClass](../../atl/reference/ccomcoclass-class.md) 는이 매크로를 포함 하 여 기본 집계 모델을 지정 합니다. 이 기본값을 재정의 하려면 클래스 정의에서 [DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) 또는 [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) 매크로 중 하나를 지정 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_classfactory"></a><a name="declare_classfactory"></a> DECLARE_CLASSFACTORY

[CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 을 클래스 팩터리로 선언 합니다.

```cpp
DECLARE_CLASSFACTORY()
```

### <a name="remarks"></a>설명

[CComCoClass](../../atl/reference/ccomcoclass-class.md) 는이 매크로를 사용 하 여 개체에 대 한 기본 클래스 팩터리를 선언 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]

## <a name="ccomclassfactory-class"></a><a name="ccomclassfactory_class"></a> CComClassFactory 클래스

이 클래스는 [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) 인터페이스를 구현 합니다.

```cpp
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>설명

`CComClassFactory` 특정 CLSID의 개체를 만드는 메서드를 포함 하는 [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) 인터페이스를 구현 하 고, 새 개체를 보다 신속 하 게 만들 수 있도록 메모리의 클래스 팩터리를 잠그는 방법을 포함 합니다. `IClassFactory` 는 시스템 레지스트리에 등록 하 고 CLSID를 할당 하는 모든 클래스에 대해 구현 되어야 합니다.

ATL 개체는 일반적으로 [CComCoClass](../../atl/reference/ccomcoclass-class.md)에서 파생 하 여 클래스 팩터리를 가져옵니다. 이 클래스에는 `CComClassFactory`를 기본 클래스 팩터리로 선언하는 매크로 [DECLARE_CLASSFACTORY](#declare_classfactory) 포함되어 있습니다. 이 기본값을 재정의 하려면 클래스 정의에서 DECLARE_CLASSFACTORY *XXX* 매크로 중 하나를 지정 합니다. 예를 들어 [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex) 매크로는 클래스 팩터리에 대해 지정 된 클래스를 사용 합니다.

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

위의 클래스 정의는 `CMyClassFactory` 가 개체의 기본 클래스 팩터리로 사용 되도록 지정 합니다. `CMyClassFactory` 에서 파생 되 `CComClassFactory` 고를 재정의 해야 합니다 `CreateInstance` .

ATL은 클래스 팩터리를 선언 하는 세 가지 다른 매크로를 제공 합니다.

- [DECLARE_CLASSFACTORY2](#declare_classfactory2) 라이선스를 통해 생성을 제어 하는 [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)을 사용 합니다.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) 는 여러 아파트에서 개체를 만드는 [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)를 사용 합니다.

- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) 단일 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) 개체를 생성 하는 [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)을 사용 합니다.

## <a name="declare_classfactory_ex"></a><a name="declare_classfactory_ex"></a> DECLARE_CLASSFACTORY_EX

`cf`를 클래스 팩터리로 선언 합니다.

```cpp
DECLARE_CLASSFACTORY_EX( cf )
```

### <a name="parameters"></a>매개 변수

*f*<br/>
진행 클래스 팩터리 개체를 구현 하는 클래스의 이름입니다.

### <a name="remarks"></a>설명

*Cf* 매개 변수는 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 에서 파생 되 고 메서드를 재정의 해야 합니다 `CreateInstance` .

[CComCoClass](../../atl/reference/ccomcoclass-class.md)에는 기본 클래스 팩터리로 `CComClassFactory` 지정하는 [DECLARE_CLASSFACTORY](#declare_classfactory) 매크로가 포함되어 있습니다. 그러나 개체의 클래스 정의에 DECLARE_CLASSFACTORY_EX 매크로를 포함 하 여이 기본값을 재정의 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

## <a name="declare_classfactory2"></a><a name="declare_classfactory2"></a> DECLARE_CLASSFACTORY2

[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) 을 클래스 팩터리로 선언 합니다.

```cpp
DECLARE_CLASSFACTORY2( lic )
```

### <a name="parameters"></a>매개 변수

*lic*<br/>
진행 , 및를 구현 하는 클래스입니다 `VerifyLicenseKey` `GetLicenseKey` `IsLicenseValid` .

### <a name="remarks"></a>설명

[CComCoClass](../../atl/reference/ccomcoclass-class.md) 에는 기본 클래스 팩터리로 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 를 지정 하는 [DECLARE_CLASSFACTORY](#declare_classfactory) 매크로가 포함 되어 있습니다. 그러나 개체의 클래스 정의에 DECLARE_CLASSFACTORY2 매크로를 포함 하 여이 기본값을 재정의 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

## <a name="ccomclassfactory2-class"></a><a name="ccomclassfactory2_class"></a> CComClassFactory2 클래스

이 클래스는 [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) 인터페이스를 구현 합니다.

```cpp
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

### <a name="parameters"></a>매개 변수

*사용권이*<br/>
다음 정적 함수를 구현 하는 클래스입니다.

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

### <a name="remarks"></a>설명

`CComClassFactory2`[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)의 확장인 [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) 인터페이스를 구현 합니다. `IClassFactory2` 라이선스를 통해 개체 생성을 제어 합니다. 사용이 허가 된 컴퓨터에서 실행 되는 클래스 팩터리는 런타임 라이선스 키를 제공할 수 있습니다. 이 라이선스 키를 사용 하면 전체 컴퓨터 라이선스가 없는 경우 응용 프로그램에서 개체를 인스턴스화할 수 있습니다.

ATL 개체는 일반적으로 [CComCoClass](../../atl/reference/ccomcoclass-class.md)에서 파생 하 여 클래스 팩터리를 가져옵니다. 이 클래스에는 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 을 기본 클래스 팩터리로 선언 하는 매크로 [DECLARE_CLASSFACTORY](#declare_classfactory)포함 되어 있습니다. 을 사용 하려면 `CComClassFactory2` 개체의 클래스 정의에 [DECLARE_CLASSFACTORY2](#declare_classfactory2) 매크로를 지정 합니다. 예를 들어:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

`CMyLicense`의 템플릿 매개 변수는 `CComClassFactory2` 정적 함수, 및를 구현 해야 합니다 `VerifyLicenseKey` `GetLicenseKey` `IsLicenseValid` . 다음은 간단한 라이선스 클래스의 예제입니다.

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]

`CComClassFactory2``CComClassFactory2Base`및 *라이선스* 모두에서 파생 됩니다. `CComClassFactory2Base`그러면는 `IClassFactory2` 및 **CComObjectRootEx \< CComGlobalsThreadModel >** 에서 파생 됩니다.

## <a name="declare_classfactory_auto_thread"></a><a name="declare_classfactory_auto_thread"></a> DECLARE_CLASSFACTORY_AUTO_THREAD

[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) 을 클래스 팩터리로 선언 합니다.

```cpp
DECLARE_CLASSFACTORY_AUTO_THREAD()
```

### <a name="remarks"></a>설명

[CComCoClass](../../atl/reference/ccomcoclass-class.md) 에는 기본 클래스 팩터리로 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 를 지정 하는 [DECLARE_CLASSFACTORY](#declare_classfactory) 매크로가 포함 되어 있습니다. 그러나 개체의 클래스 정의에 DECLARE_CLASSFACTORY_AUTO_THREAD 매크로를 포함 하 여이 기본값을 재정의 합니다.

여러 아파트에서 개체를 만들 때 (in-proc 서버에서) 클래스에 DECLARE_CLASSFACTORY_AUTO_THREAD를 추가 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="ccomclassfactoryautothread-class"></a><a name="ccomclassfactoryautothread_class"></a> CComClassFactoryAutoThread 클래스

이 클래스는 [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) 인터페이스를 구현 하 고 여러 아파트에서 개체를 만들 수 있도록 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

```cpp
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>설명

`CComClassFactoryAutoThread` 는 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)와 유사 하지만 여러 아파트에서 개체를 만들 수 있습니다. 이 지원을 활용 하려면 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)에서 EXE 모듈을 파생 시키십시오.

ATL 개체는 일반적으로 [CComCoClass](../../atl/reference/ccomcoclass-class.md)에서 파생 하 여 클래스 팩터리를 가져옵니다. 이 클래스에는 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 을 기본 클래스 팩터리로 선언 하는 매크로 [DECLARE_CLASSFACTORY](#declare_classfactory)포함 되어 있습니다. 을 사용 하려면 `CComClassFactoryAutoThread` 개체의 클래스 정의에 [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) 매크로를 지정 합니다. 예를 들어:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="declare_classfactory_singleton"></a><a name="declare_classfactory_singleton"></a> DECLARE_CLASSFACTORY_SINGLETON

[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) 을 클래스 팩터리로 선언 합니다.

```cpp
DECLARE_CLASSFACTORY_SINGLETON( obj )
```

### <a name="parameters"></a>매개 변수

*obj*<br/>
진행 클래스 개체의 이름입니다.

### <a name="remarks"></a>설명

[CComCoClass](../../atl/reference/ccomcoclass-class.md) 에는 기본 클래스 팩터리로 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 를 지정 하는 [DECLARE_CLASSFACTORY](#declare_classfactory) 매크로가 포함 되어 있습니다. 그러나 개체의 클래스 정의에 DECLARE_CLASSFACTORY_SINGLETON 매크로를 포함 하 여이 기본값을 재정의 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="ccomclassfactorysingleton-class"></a><a name="ccomclassfactorysingleton_class"></a> CComClassFactorySingleton 클래스

이 클래스는 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 에서 파생 되며 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) 를 사용 하 여 단일 개체를 생성 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

```cpp
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

### <a name="parameters"></a>매개 변수

*T*<br/>
클래스입니다.

`CComClassFactorySingleton`[CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 에서 파생 되 고 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) 를 사용 하 여 단일 개체를 생성 합니다. 메서드를 호출할 때마다 `CreateInstance` 인터페이스 포인터에 대해이 개체를 쿼리 하기만 합니다.

### <a name="remarks"></a>설명

ATL 개체는 일반적으로 [CComCoClass](../../atl/reference/ccomcoclass-class.md)에서 파생 하 여 클래스 팩터리를 가져옵니다. 이 클래스에는 `CComClassFactory`를 기본 클래스 팩터리로 선언하는 매크로 [DECLARE_CLASSFACTORY](#declare_classfactory) 포함되어 있습니다. 을 사용 하려면 `CComClassFactorySingleton` 개체의 클래스 정의에 [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) 매크로를 지정 합니다. 예를 들어:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="declare_get_controlling_unknown"></a><a name="declare_get_controlling_unknown"></a> DECLARE_GET_CONTROLLING_UNKNOWN

가상 함수를 선언 `GetControllingUnknown` 합니다.

```cpp
DECLARE_GET_CONTROLLING_UNKNOWN()
```

### <a name="remarks"></a>설명

에서와 같이 정의 되지 않은 컴파일러 오류 메시지가 표시 되는 경우이 매크로를 개체에 추가 `GetControllingUnknown` `CComAggregateCreator` 합니다.

## <a name="declare_not_aggregatable"></a><a name="declare_not_aggregatable"></a> DECLARE_NOT_AGGREGATABLE

개체를 집계할 수 없도록 지정 합니다.

```cpp
DECLARE_NOT_AGGREGATABLE( x )
```

### <a name="parameters"></a>매개 변수

*x*<br/>
진행 집계할 수 없는 것으로 정의 하는 클래스 개체의 이름입니다.

### <a name="remarks"></a>설명

개체에 대 한 `CreateInstance` 집계를 시도 하는 경우 DECLARE_NOT_AGGREGATABLE에서 오류 (CLASS_E_NOAGGREGATION)를 반환 합니다.

기본적으로 [CComCoClass](../../atl/reference/ccomcoclass-class.md) 에는 개체를 집계할 수 있도록 지정 하는 [DECLARE_AGGREGATABLE](#declare_aggregatable) 매크로가 포함 되어 있습니다. 이 기본 동작을 재정의 하려면 클래스 정의에 DECLARE_NOT_AGGREGATABLE를 포함 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_only_aggregatable"></a><a name="declare_only_aggregatable"></a> DECLARE_ONLY_AGGREGATABLE

개체를 집계 하도록 지정 합니다.

```cpp
DECLARE_ONLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>매개 변수

*x*<br/>
진행 집계할 수 있는 것으로 정의 하는 클래스 개체의 이름입니다.

### <a name="remarks"></a>설명

개체를 집계할 수 없는 개체로 만들려고 하면 오류가 발생 DECLARE_ONLY_AGGREGATABLE (E_FAIL) `CoCreate` .

기본적으로 [CComCoClass](../../atl/reference/ccomcoclass-class.md) 에는 개체를 집계할 수 있도록 지정 하는 [DECLARE_AGGREGATABLE](#declare_aggregatable) 매크로가 포함 되어 있습니다. 이 기본 동작을 재정의 하려면 클래스 정의에 DECLARE_ONLY_AGGREGATABLE를 포함 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]

## <a name="declare_poly_aggregatable"></a><a name="declare_poly_aggregatable"></a> DECLARE_POLY_AGGREGATABLE

개체를 만들 때 **Ccompolyobject \<** *x* **>** 의 인스턴스를 만들도록 지정 합니다.

```cpp
DECLARE_POLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>매개 변수

*x*<br/>
진행 집계할 수 있는 것으로 정의 하거나 집계할 수 없는 클래스 개체의 이름입니다.

### <a name="remarks"></a>설명

생성 하는 동안 알 수 없는 외부 값이 확인 됩니다. NULL 인 경우 `IUnknown` 는 집계할 수 없는 개체에 대해 구현 됩니다. 외부 unknown이 NULL이 아닌 경우는 `IUnknown` 집계 된 개체에 대해 구현 됩니다.

DECLARE_POLY_AGGREGATABLE를 사용 하는 경우의 장점은 집계 된 사례와 집계할 수 없는 `CComAggObject` 사례를 `CComObject` 처리 하기 위해 모듈에서 및를 모두 사용 하지 않도록 하는 것입니다. 단일 `CComPolyObject` 개체는 두 경우를 모두 처리 합니다. 즉, 모듈에는 vtable의 복사본 하 나와 함수의 복사본이 하나만 있습니다. Vtable이 큰 경우 모듈 크기를 크게 줄일 수 있습니다. 그러나 vtable이 작은 경우를 사용 하면 `CComPolyObject` 집계 된 개체 또는 집계할 수 없는 개체에 대해 최적화 되지 않으므로를 사용 하 여 모듈 크기가 약간 커질 수 있습니다 `CComAggObject` `CComObject` .

ATL 컨트롤 마법사를 사용 하 여 모든 컨트롤을 만드는 경우 DECLARE_POLY_AGGREGATABLE 매크로가 개체에 자동으로 선언 됩니다.

## <a name="declare_protect_final_construct"></a><a name="declare_protect_final_construct"></a> DECLARE_PROTECT_FINAL_CONSTRUCT

개체를 삭제 하지 않도록 보호 합니다. ( [가 중이](ccomobjectrootex-class.md#finalconstruct)아닌 경우) 내부 집계 된 개체가 참조 횟수를 증가 시킨 다음 개수를 0으로 감소 시킵니다.

```cpp
DECLARE_PROTECT_FINAL_CONSTRUCT()
```

## <a name="declare_view_status"></a><a name="declare_view_status"></a> DECLARE_VIEW_STATUS

이 매크로를 ATL ActiveX 컨트롤의 컨트롤 클래스에 삽입 하 여 컨테이너에 VIEWSTATUS 플래그를 지정 합니다.

```cpp
DECLARE_VIEW_STATUS( statusFlags )
```

### <a name="parameters"></a>매개 변수

*statusFlags*<br/>
진행 VIEWSTATUS 플래그입니다. 플래그 목록은 [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) 를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]

## <a name="see-also"></a>참고 항목

[매크로](../../atl/reference/atl-macros.md)
