---
description: '자세한 정보: CStrBufT 클래스'
title: CStrBufT 클래스
ms.date: 10/18/2018
f1_keywords:
- CStrBufT
- ATLSIMPSTR/ATL::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::SetLength
- ATLSIMPSTR/ATL::CStrBufT::AUTO_LENGTH
- ATLSIMPSTR/ATL::CStrBufT::SET_LENGTH
helpviewer_keywords:
- strings [C++], custom memory management
- CStrBufT class
- shared classes, CStrBufT
ms.assetid: 6b50fa8f-87e8-4ed4-a229-157ce128710f
ms.openlocfilehash: 4cc38f13d740b7def65c6f958d53af7b367adcb6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166618"
---
# <a name="cstrbuft-class"></a>CStrBufT 클래스

이 클래스는 기존 개체에 대 한 및 호출에 대 한 자동 리소스 정리를 제공 `GetBuffer` `ReleaseBuffer` `CStringT` 합니다.

## <a name="syntax"></a>구문

```
template<typename TCharType>
class CStrBufT
```

#### <a name="parameters"></a>매개 변수

*TCharType*<br/>
클래스의 문자 형식 `CStrBufT` 입니다. 다음 중 하나일 수 있습니다.

- **`char`** (ANSI 문자열의 경우)

- **`wchar_t`** (유니코드 문자열의 경우)

- TCHAR.H (ANSI 및 유니코드 문자열 모두)

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|PCXSTR|상수 문자열에 대 한 포인터입니다.|
|PXSTR|문자열에 대 한 포인터입니다.|
|`StringType`|이 클래스 템플릿의 특수화에서 해당 버퍼를 조작할 문자열 형식입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CStrBufT:: CStrBufT](#cstrbuft)|문자열 버퍼 개체의 생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CStrBufT:: SetLength](#setlength)|연결 된 문자열 개체의 문자 버퍼 길이를 설정 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CStrBufT:: operator PCXSTR](#operator_pcxstr)|연결 된 **`const`** 문자열 개체의 문자 버퍼에 대 한 포인터를 검색 합니다.|
|[CStrBufT:: operator PXSTR](#operator_pxstr)|연결 된 문자열 개체의 문자 버퍼에 대 한 포인터를 검색 합니다.|

### <a name="public-constants"></a>공용 상수

|Name|설명|
|----------|-----------------|
|[CStrBufT:: AUTO_LENGTH](#auto_length)|릴리스에서 새 문자열 길이를 자동으로 결정 합니다.|
|[CStrBufT:: SET_LENGTH](#set_length)|GetBuffer 시간에 문자열 개체의 길이를 설정 합니다.|

## <a name="remarks"></a>설명

이 클래스는 [getbuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) 및 [Releasebuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)또는 [GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) 및에 대 한 호출을 대체 하기 위한 래퍼 클래스로 사용 됩니다 `ReleaseBuffer` .

주로 도우미 클래스로 디자인 된는 `CStrBufT` 개발자가를 호출 하는 방법 또는 시기를 걱정 하지 않고 문자열 개체의 문자 버퍼로 작업할 수 있는 편리한 방법을 제공 합니다 `ReleaseBuffer` . 이는 래퍼 개체가 예외 또는 여러 개의 종료 된 코드 경로에서 본질적으로 범위를 벗어나기 때문에 가능 합니다. 소멸자가 문자열 리소스를 해제 하도록 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** atlsimpstr

## <a name="cstrbuftauto_length"></a><a name="auto_length"></a> CStrBufT:: AUTO_LENGTH

릴리스에서 새 문자열 길이를 자동으로 결정 합니다.

```
static const DWORD AUTO_LENGTH = 0x01;
```

### <a name="remarks"></a>설명

릴리스에서 새 문자열 길이를 자동으로 결정 합니다. 문자열은 null로 종결 되어야 합니다.

## <a name="cstrbuftcstrbuft"></a><a name="cstrbuft"></a> CStrBufT:: CStrBufT

버퍼 개체를 생성 합니다.

```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```

### <a name="parameters"></a>매개 변수

*str*<br/>
버퍼와 연결 된 문자열 개체입니다. 일반적으로 개발자는 `CStrBuf` (tchar.h 변형), ( `CStrBufA` **`char`** variant) 및 `CStrBufW` ( **`wchar_t`** variant)의 미리 정의 된 typedef를 사용 합니다.

*nMinLength*<br/>
문자 버퍼의 최소 길이입니다.

*dwFlags*<br/>
문자열 길이가 자동으로 결정 되는지 여부를 결정 합니다. 다음 중 하나일 수 있습니다.

- AUTO_LENGTH 문자열 길이는 [CSimpleStringT:: Release](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) 가 호출 될 때 자동으로 결정 됩니다. 문자열은 null로 종결 되어야 합니다. 기본값입니다.

- [CSimpleStringT:: GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) 를 호출 하면 SET_LENGTH 문자열 길이가 설정 됩니다.

### <a name="remarks"></a>설명

연결 된 문자열 개체에 대 한 문자열 버퍼를 만듭니다. 생성 하는 동안 [CSimpleStringT:: GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) 또는 [CSimpleStringT:: GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) 를 호출 합니다.

복사 생성자는 **`private`** 입니다.

## <a name="cstrbuftoperator-pcxstr"></a><a name="operator_pcxstr"></a> CStrBufT:: operator PCXSTR

연결 된 문자열 개체에 저장 된 문자를 C 스타일 문자열로 직접 액세스 합니다.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>반환 값

문자열 데이터에 대 한 문자 포인터입니다.

### <a name="remarks"></a>설명

문자열 개체의 문자 버퍼에 대 한 포인터를 반환 하려면이 함수를 호출 합니다. 문자열 개체의 내용은이 포인터를 사용 하 여 변경할 수 없습니다.

## <a name="cstrbuftoperator-pxstr"></a><a name="operator_pxstr"></a> CStrBufT:: operator PXSTR

연결 된 문자열 개체에 저장 된 문자를 C 스타일 문자열로 직접 액세스 합니다.

```
operator PXSTR() throw();
```

### <a name="return-value"></a>반환 값

문자열 데이터에 대 한 문자 포인터입니다.

### <a name="remarks"></a>설명

문자열 개체의 문자 버퍼에 대 한 포인터를 반환 하려면이 함수를 호출 합니다. 개발자는이 포인터를 사용 하 여 문자열 개체의 내용을 변경할 수 있습니다.

## <a name="cstrbuftpcxstr"></a><a name="pcxstr"></a> CStrBufT::P CXSTR

상수 문자열에 대 한 포인터입니다.

```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```

## <a name="cstrbuftpxstr"></a><a name="pxstr"></a> CStrBufT::P XSTR

문자열에 대 한 포인터입니다.

```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```

## <a name="cstrbuftset_length"></a><a name="set_length"></a> CStrBufT:: SET_LENGTH

문자열 개체의 길이를 시간에 설정 `GetBuffer` 합니다.

```
static const DWORD SET_LENGTH = 0x02;
```

### <a name="remarks"></a>설명

GetBuffer 시간에 문자열 개체의 길이를 설정 합니다.

문자열 버퍼 개체가 생성 될 때 [CSimpleStringT:: GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) 및 [CSimpleStringT:: GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) 가 호출 되는지 여부를 결정 합니다.

## <a name="cstrbuftsetlength"></a><a name="setlength"></a> CStrBufT:: SetLength

문자 버퍼의 길이를 설정 합니다.

```cpp
void SetLength(int nLength);
```

### <a name="parameters"></a>매개 변수

*nLength*<br/>
문자열 개체에 대 한 문자 버퍼의 새 길이입니다.

> [!NOTE]
> 는의 생성자에 지정 된 최소 버퍼 길이 보다 작거나 같아야 합니다 `CStrBufT` .

### <a name="remarks"></a>설명

이 함수를 호출 하 여 buffer 개체가 나타내는 문자열의 길이를 설정 합니다.

## <a name="cstrbuftstringtype"></a><a name="stringtype"></a> CStrBufT:: StringType

이 클래스 템플릿의 특수화에서 해당 버퍼를 조작할 문자열 형식입니다.

```
typedef CSimpleStringT<TCharType> StringType;
```

### <a name="remarks"></a>설명

`TCharType` 클래스 템플릿을 특수화 하는 데 사용 되는 문자 형식입니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 공유 클래스](../../atl-mfc-shared/atl-mfc-shared-classes.md)
