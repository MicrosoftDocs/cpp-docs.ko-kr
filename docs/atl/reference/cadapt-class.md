---
description: '자세히 알아보기: CAdapt 클래스'
title: CAdapt 클래스
ms.date: 11/04/2016
f1_keywords:
- CAdapt
- ATLCOMCLI/ATL::CAdapt
- ATLCOMCLI/ATL::CAdapt::CAdapt
- ATLCOMCLI/ATL::CAdapt::m_T
helpviewer_keywords:
- address-of operator
- adapter objects
- '& operator, address-of operator'
- CAdapt class
ms.assetid: 0bb695a5-72fe-43d1-8f39-7e4da6e34765
ms.openlocfilehash: 6c6ec1c40d430c2de64defb5ea7394a47b1d7a6f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158506"
---
# <a name="cadapt-class"></a>CAdapt 클래스

이 템플릿은 개체 주소 이외의 주소를 반환하도록 연산자 주소를 다시 정의하는 클래스를 래핑하는 데 사용됩니다.

## <a name="syntax"></a>구문

```cpp
template <class T>
class CAdapt
```

### <a name="parameters"></a>매개 변수

*T*<br/>
조정된 형식입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAdapt:: CAdapt](#cadapt)|생성자입니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CAdapt:: operator const T&](#operator_const_t_amp)|**`const`** 에 대 한 참조를 반환 `m_T` 합니다.|
|[CAdapt:: operator T&](#operator_t_amp)|`m_T`에 대한 참조를 반환합니다.|
|[CAdapt:: operator <](#operator_lt)|조정된 형식의 개체를 `m_T`와 비교합니다.|
|[CAdapt:: operator =](#operator_eq)|조정된 형식의 개체를 `m_T`에 할당합니다.|
|[CAdapt:: operator = =](#operator_eq_eq)|조정된 형식의 개체를 `m_T`와 비교합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CAdapt:: m_T](#m_t)|조정되는 데이터입니다.|

## <a name="remarks"></a>설명

`CAdapt`는 개체의 주소 이외의 주소를 반환하도록 연산자의 주소(`operator &`)를 다시 정의하는 클래스를 래핑하는 데 사용되는 간단한 템플릿입니다. 이러한 클래스의 예로 ATL의 `CComBSTR`, `CComPtr`, `CComQIPtr` 클래스 및 컴파일러 COM 지원 클래스인 `_com_ptr_t`가 있습니다. 이러한 클래스는 모두 데이터 멤버 중 하나의 주소를 반환 하도록 연산자 주소를 다시 정의 합니다 (의 경우 BSTR `CComBSTR` , 다른 클래스의 경우 인터페이스 포인터).

`CAdapt`의 주 역할은 클래스 *T* 에서 정의한 연산자의 주소를 숨기는 것 이지만 여전히 조정 된 클래스의 특성을 유지 합니다. `CAdapt`*t* 형식의 public 멤버 [m_T](#m_t)를 유지 하 고, 변환 연산자, 비교 연산자 및 복사 생성자를 정의 하 여의 특수화가 `CAdapt` *t* 형식의 개체인 것 처럼 처리 될 수 있도록 하는 방식으로이 역할을 되도록 합니다.

어댑터 클래스 `CAdapt`는 일부 컨테이너 스타일 클래스가 연산자 주소를 사용하여 포함된 개체의 주소를 가져올 수 있기 때문에 유용합니다. 연산자의 주소를 다시 정의하면 일반적으로 컴파일 오류가 발생하고 "작동"해야 하는 클래스에서 조정되지 않은 형식이 사용되지 않아 이 요구 사항에 맞지 않게 됩니다. `CAdapt`가 이러한 문제에 대한 해결 방법을 제공합니다.

일반적으로 컨테이너 스타일 클래스에 `CAdapt`, `CComBSTR`, `CComPtr` 또는 `CComQIPtr` 개체를 저장하려는 경우 `_com_ptr_t`를 사용합니다. 이는 C++11 표준이 지원되기 전에 C++ 표준 라이브러리 컨테이너에 대해 가장 일반적으로 필요했지만, 이제 C++11 표준 라이브러리 컨테이너가 `operator&()`를 오버로드한 형식으로 자동으로 작동합니다. 표준 라이브러리는 내부적으로 [std:: addressof](../../standard-library/memory-functions.md#addressof) 를 사용 하 여 개체의 실제 주소를 가져옵니다.

## <a name="requirements"></a>요구 사항

**헤더:** comcli .h

## <a name="cadaptcadapt"></a><a name="cadapt"></a> CAdapt:: CAdapt

생성자를 사용 하면 어댑터 개체를 기본으로 생성 하거나, 조정 된 형식의 개체에서 복사 하거나, 다른 어댑터 개체에서 복사할 수 있습니다.

```cpp
CAdapt();
CAdapt(const T& rSrc);
CAdapt(const CAdapt& rSrCA);
CAdapt(T&& rSrCA);  // (Visual Studio 2017)
CAdapt(CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>매개 변수

*.Rsrc*<br/>
새로 생성 된 어댑터 개체에 복사 하도록 조정 되는 형식의 변수입니다.

*rSrCA*<br/>
포함 된 데이터를 새로 생성 된 어댑터 개체로 복사 또는 이동 해야 하는 어댑터 개체입니다.

## <a name="cadaptm_t"></a><a name="m_t"></a> CAdapt:: m_T

조정 되는 데이터를 보유 합니다.

```cpp
T m_T;
```

### <a name="remarks"></a>설명

이 **`public`** 데이터 멤버는 [연산자 const t&](#operator_const_t_amp) 및 [operator t&](#operator_t_amp)를 사용 하 여 직접 또는 간접적으로 액세스할 수 있습니다.

## <a name="cadaptoperator-const-tamp"></a><a name="operator_const_t_amp"></a> CAdapt:: operator const T&amp;

**`const`** [M_T](#m_t) 멤버에 대 한 참조를 반환 하 여 어댑터 개체가 *T* 형식의 개체인 것 처럼 처리 될 수 있도록 합니다.

```cpp
operator const T&() const;
```

### <a name="return-value"></a>반환 값

**`const`** 에 대 한 참조 `m_T` 입니다.

## <a name="cadaptoperator-tamp"></a><a name="operator_t_amp"></a> CAdapt:: operator T&amp;

[M_T](#m_t) 멤버에 대 한 참조를 반환 하 여 어댑터 개체가 *T* 형식의 개체인 것 처럼 처리 될 수 있도록 합니다.

```cpp
operator T&();
```

### <a name="return-value"></a>반환 값

`m_T`에 대한 참조입니다.

## <a name="cadaptoperator-lt"></a><a name="operator_lt"></a> CAdapt:: 연산자 &lt;

조정 된 형식의 개체를 [m_T](#m_t)와 비교 합니다.

```cpp
bool operator<(const T& rSrc) const;
```

### <a name="parameters"></a>매개 변수

*.Rsrc*<br/>
비교할 개체에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

`m_T`과 *rsrc* 간의 비교 결과입니다.

## <a name="cadaptoperator-"></a><a name="operator_eq"></a> CAdapt:: operator =

대입 연산자는 *Rsrc* 라는 인수를 데이터 멤버 [m_T](#m_t) 에 할당 하 고 현재 어댑터 개체를 반환 합니다.

```cpp
CAdapt& operator= (const T& rSrc);
CAdapt& operator= (T&& rSrCA); // (Visual Studio 2017)
CAdapt& operator= (CAdapt<T>&& rSrCA) noexcept; // (Visual Studio 2017)
```

### <a name="parameters"></a>매개 변수

*.Rsrc*<br/>
복사할 조정 된 형식의 개체에 대 한 참조입니다.

*rSrCA*<br/>
이동할 개체에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

현재 개체에 대 한 참조입니다.

## <a name="cadaptoperator-"></a><a name="operator_eq_eq"></a> CAdapt:: operator = =

조정 된 형식의 개체를 [m_T](#m_t)와 비교 합니다.

```cpp
bool operator== (const T& rSrc) const;
```

### <a name="parameters"></a>매개 변수

*.Rsrc*<br/>
비교할 개체에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

*M_T* 와 *rsrc* 간의 비교 결과입니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
