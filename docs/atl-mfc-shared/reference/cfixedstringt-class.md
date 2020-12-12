---
description: CFixedStringT 클래스에 대해 자세히 알아보세요.
title: CFixedStringT 클래스
ms.date: 03/27/2019
f1_keywords:
- CFixedStringT
- CSTRINGT/ATL::CFixedStringT
- CSTRINGT/ATL::CFixedStringT::CFixedStringT
helpviewer_keywords:
- CFixedStringT class
- shared classes, CFixedStringT
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
ms.openlocfilehash: a613716364318ced140709d2b33e9d9c4299af0b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166838"
---
# <a name="cfixedstringt-class"></a>CFixedStringT 클래스

이 클래스는 고정 문자 버퍼를 사용 하는 문자열 개체를 나타냅니다.

## <a name="syntax"></a>구문

```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```

#### <a name="parameters"></a>매개 변수

*StringType*<br/>
고정 문자열 개체에 대 한 기본 클래스로 사용 되며 임의의 `CStringT` 기반 형식일 수 있습니다. 몇 가지 예 `CString` 를 들면, `CStringA` 및가 `CStringW` 있습니다.

*t_nChars*<br/>
버퍼에 저장 된 문자 수입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CFixedStringT:: CFixedStringT](#cfixedstringt)|문자열 개체에 대 한 생성자입니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CFixedStringT:: operator =](#operator_eq)|개체에 새 값을 할당 `CFixedStringT` 합니다.|

## <a name="remarks"></a>설명

이 클래스는을 기반으로 하는 사용자 지정 문자열 클래스의 예제입니다 `CStringT` . 이와 유사 하지만 두 클래스는 구현에 따라 다릅니다. 와 간의 주요 차이점 `CFixedStringT` 은 `CStringT` 다음과 같습니다.

- 초기 문자 버퍼는 개체의 일부로 할당 되 고 *t_nChars* 크기가 있습니다. 이렇게 하면 `CFixedString` 개체가 성능상의 이유로 인접 한 메모리 청크를 차지할 수 있습니다. 그러나 개체의 내용이 `CFixedStringT` *t_nChars* 보다 커지면 버퍼가 동적으로 할당 됩니다.

- 개체의 문자 버퍼는 `CFixedStringT` 항상 같은 길이 ( *t_nChars*)입니다. 개체의 버퍼 크기에 대 한 제한은 없습니다 `CStringT` .

- 의 메모리 관리자는 `CFixedStringT` 두 개 이상의 개체 간에 [CStringData](../../atl-mfc-shared/reference/cstringdata-class.md) 개체를 공유할 수 없도록 사용자 지정 됩니다 `CFixedStringT` . `CStringT` 개체에는 이러한 제한이 없습니다.

일반적으로 문자열 개체에 대 한 및 메모리 관리를 사용자 지정 하는 방법에 대 한 자세한 내용은 `CFixedStringT` [메모리 관리 및 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)를 참조 하십시오.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IAtlStringMgr`

`StringType`

`CFixedStringMgr`

`CFixedStringT`

## <a name="requirements"></a>요구 사항

**헤더:** cstringt. h

## <a name="cfixedstringtcfixedstringt"></a><a name="cfixedstringt"></a> CFixedStringT:: CFixedStringT

`CFixedStringT` 개체를 생성합니다.

```
CFixedStringT() throw();
explicit CFixedStringT(IAtlStringMgr* pStringMgr) throw();
CFixedStringT(const CFixedStringT<StringType, t_nChars>& strSrc);
CFixedStringT(const StringType& strSrc);
CFixedStringT(const StringType::XCHAR* pszSrc);
explicit CFixedStringT(const StringType::YCHAR* pszSrc);
explicit CFixedStringT(const unsigned char* pszSrc);
```

### <a name="parameters"></a>매개 변수

*pszSrc*<br/>
이 개체로 복사 될 null로 끝나는 문자열 `CFixedStringT` 입니다.

*strSrc*<br/>
`CFixedStringT`이 개체에 복사할 기존 개체 `CFixedStringT` 입니다.

*pStringMgr*<br/>
개체의 메모리 관리자에 대 한 포인터 `CFixedStringT` 입니다. 및의 메모리 관리에 대 한 자세한 내용은 `IAtlStringMgr` `CFixedStringT` [메모리 관리 및 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)를 참조 하십시오.

### <a name="remarks"></a>설명

생성자는 입력 데이터를 새 할당 된 저장소에 복사 하기 때문에 메모리 예외가 발생할 수 있음을 알고 있어야 합니다. 이러한 생성자 중 일부는 변환 함수 역할을 합니다.

## <a name="cfixedstringtoperator-"></a><a name="operator_eq"></a> CFixedStringT:: operator =

`CFixedStringT`새 데이터를 사용 하 여 기존 개체를 다시 초기화 합니다.

```
CFixedStringT<StringType, t_nChars>& operator=(
    const CFixedStringT<StringType, t_nChars>& strSrc);
CFixedStringT<StringType, t_nChars>& operator=(const char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const wchar_t* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const unsigned char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const StringType& strSrc);
```

### <a name="parameters"></a>매개 변수

*pszSrc*<br/>
이 개체로 복사 될 null로 끝나는 문자열 `CFixedStringT` 입니다.

*strSrc*<br/>
`CFixedStringT`이 개체에 복사 되는 기존 `CFixedStringT` 입니다.

### <a name="remarks"></a>설명

할당 연산자를 사용할 때마다 메모리 예외가 발생할 수 있다는 점에 유의 해야 합니다. 새 저장소는 일반적으로 결과 개체를 보유 하기 위해 할당 되기 때문입니다 `CFixedStringT` .

## <a name="see-also"></a>참고 항목

[CStringT 클래스](../../atl-mfc-shared/reference/cstringt-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 공유 클래스](../../atl-mfc-shared/atl-mfc-shared-classes.md)
