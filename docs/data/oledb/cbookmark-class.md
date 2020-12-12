---
description: '자세히 알아보기: CBookmark 클래스'
title: CBookmark 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL.CBookmark
- ATL::CBookmark<nSize>
- CBookmark
- ATL.CBookmark<nSize>
- ATL::CBookmark
- CBookmark<0>.CBookmark<0>
- CBookmark::CBookmark
- ATL.CBookmark.CBookmark
- CBookmark.CBookmark
- ATL::CBookmark<0>::CBookmark<0>
- ATL.CBookmark<0>.CBookmark<0>
- CBookmark<0>::CBookmark<0>
- ATL::CBookmark::CBookmark
- ATL.CBookmark<0>.GetBuffer
- ATL.CBookmark.GetBuffer
- ATL::CBookmark<0>::GetBuffer
- ATL::CBookmark::GetBuffer
- CBookmark.GetBuffer
- ATL::CBookmark<nSize>::GetBuffer
- ATL.CBookmark<nSize>.GetBuffer
- CBookmark<0>.GetBuffer
- CBookmark<nSize>::GetBuffer
- CBookmark<0>::GetBuffer
- CBookmark<nSize>.GetBuffer
- CBookmark::GetBuffer
- CBookmark::GetSize
- ATL.CBookmark<nSize>.GetSize
- CBookmark<nSize>.GetSize
- CBookmark.GetSize
- ATL::CBookmark::GetSize
- CBookmark<0>::GetSize
- ATL::CBookmark<nSize>::GetSize
- ATL.CBookmark<0>.GetSize
- ATL::CBookmark<0>::GetSize
- ATL.CBookmark.GetSize
- CBookmark<0>.GetSize
- CBookmark<nSize>::GetSize
- CBookmark<0>::SetBookmark
- ATL.CBookmark<0>.SetBookmark
- CBookmark<0>.SetBookmark
- SetBookmark
- ATL::CBookmark::SetBookmark
- ATL::CBookmark<0>::SetBookmark
- CBookmark.SetBookmark
- ATL.CBookmark.SetBookmark
- CBookmark::SetBookmark
- CBookmark<0>::operator=
- CBookmark<0>.operator=
- ATL.CBookmark.operator=
- CBookmark::operator=
- ATL.CBookmark<0>.operator=
- ATL::CBookmark<0>::operator=
- CBookmark.operator=
- ATL::CBookmark::operator=
helpviewer_keywords:
- CBookmark class
- CBookmark class, constructor
- GetBuffer method
- GetSize method
- SetBookmark method
- = operator, with OLE DB templates
- operator =, bookmarks
- operator=, bookmarks
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
ms.openlocfilehash: 7c138776e282c287eb7e7e09b93196ac0792f7ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295070"
---
# <a name="cbookmark-class"></a>CBookmark 클래스

는 해당 버퍼에 책갈피 값을 포함 합니다.

## <a name="syntax"></a>구문

```cpp
template < DBLENGTH nSize = 0 >
class CBookmark : public CBookmarkBase

template <>
class CBookmark< 0 > : public CBookmarkBase
```

### <a name="parameters"></a>매개 변수

*nSize*<br/>
책갈피 버퍼의 크기 (바이트)입니다. *NSize* 가 0 인 경우 책갈피 버퍼는 런타임에 동적으로 생성 됩니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldbcli.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[CBookmark](#cbookmark)|생성자|
|[GetBuffer](#getbuffer)|버퍼에 대 한 포인터를 검색 합니다.|
|[GetSize](#getsize)|버퍼의 크기 (바이트)를 검색 합니다.|
|[SetBookmark](#setbookmark)|책갈피 값을 설정 합니다.|

### <a name="operators"></a>연산자

| Name | 설명 |
|-|-|
|[연산자 =](#operator)|한 `CBookmark` 클래스를 다른 클래스에 할당 합니다.|

## <a name="remarks"></a>설명

`CBookmark<0>` 는의 템플릿 특수화 `CBookmark` 입니다. 해당 버퍼는 런타임에 동적으로 만들어집니다.

## <a name="cbookmarkcbookmark"></a><a name="cbookmark"></a> CBookmark:: CBookmark

생성자입니다.

### <a name="syntax"></a>구문

```cpp
CBookmark();
CBookmark(DBLENGTH nSize);
```

#### <a name="parameters"></a>매개 변수

*nSize*<br/>
진행 책갈피 버퍼의 크기 (바이트)입니다.

### <a name="remarks"></a>설명

첫 번째 함수는 버퍼를 NULL로 설정 하 고 버퍼 크기를 0으로 설정 합니다. 두 번째 함수는 버퍼 크기를 *nSize* 로 설정 하 고 버퍼를 *nSize* bytes의 바이트 배열로 설정 합니다.

> [!NOTE]
> 이 함수는 에서만 사용할 수 있습니다 `CBookmark<0>` .

## <a name="cbookmarkgetbuffer"></a><a name="getbuffer"></a> CBookmark:: GetBuffer

책갈피 버퍼에 대 한 포인터를 검색 합니다.

### <a name="syntax"></a>구문

```cpp
virtual BYTE* GetBuffer() const throw();
```

### <a name="return-value"></a>Return Value

책갈피 버퍼에 대 한 포인터입니다.

## <a name="cbookmarkgetsize"></a><a name="getsize"></a> CBookmark:: GetSize

책갈피 버퍼의 크기를 검색 합니다.

### <a name="syntax"></a>구문

```cpp
virtual DBLENGTH GetSize() const throw();
```

### <a name="return-value"></a>Return Value

버퍼 크기(바이트)입니다.

## <a name="cbookmarksetbookmark"></a><a name="setbookmark"></a> CBookmark:: SetBookmark

*Pbuffer* 에서 참조 하는 책갈피 값을 버퍼에 복사 하 `CBookmark` 고 버퍼 크기를 *nSize* 로 설정 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT SetBookmark(DBLENGTH nSize, BYTE* pBuffer) throw();
```

#### <a name="parameters"></a>매개 변수

*nSize*<br/>
진행 책갈피 버퍼의 크기입니다.

*pBuffer*<br/>
진행 책갈피 값을 포함 하는 바이트 배열에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

이 함수는 에서만 사용할 수 있습니다 `CBookmark<0>` .

## <a name="cbookmarkoperator-"></a><a name="operator"></a> CBookmark:: operator =

개체를 `CBookmark` 다른에 할당 합니다.

### <a name="syntax"></a>구문

```cpp
CBookmark& operator =(const CBookmark& bookmark) throw();
```

### <a name="remarks"></a>설명

이 연산자는 에서만 필요 `CBookmark<0>` 합니다.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)
