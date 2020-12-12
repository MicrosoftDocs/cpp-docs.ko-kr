---
description: '자세히 알아보기: istrstream 클래스'
title: istrstream 클래스
ms.date: 11/04/2016
f1_keywords:
- strstream/std::istrstream::rdbuf
- strstream/std::istrstream::str
helpviewer_keywords:
- istrstream class
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
ms.openlocfilehash: 45e60878c63c30daca85924a9d0091e202387b55
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306653"
---
# <a name="istrstream-class"></a>istrstream 클래스

[strstreambuf](../standard-library/strstreambuf-class.md) 클래스의 스트림 버퍼에서 요소 및 인코드된 개체의 추출을 제어하는 개체를 설명합니다.

## <a name="syntax"></a>구문

```cpp
class istrstream : public istream
```

## <a name="remarks"></a>설명

이 개체는 `strstreambuf` 클래스의 개체를 저장합니다.

> [!NOTE]
> 이 클래스는 사용되지 않습니다. 대신 [istringstream](../standard-library/sstream-typedefs.md#istringstream) 또는 [wistringstream](../standard-library/sstream-typedefs.md#wistringstream)을 사용하는 것이 좋습니다.

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[istrstream](#istrstream)|`istrstream` 형식의 개체를 생성합니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[rdbuf](#rdbuf)|스트림의 연결된 `strstreambuf` 개체에 대한 포인터를 반환합니다.|
|[str](#str)|[freeze](../standard-library/strstreambuf-class.md#freeze)를 호출한 다음 제어되는 시퀀스의 시작 부분에 대한 포인터를 반환합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<strstream>

**네임스페이스:** std

## <a name="istrstreamistrstream"></a><a name="istrstream"></a> istrstream:: istrstream

`istrstream` 형식의 개체를 생성합니다.

```cpp
explicit istrstream(
    const char* ptr);

explicit istrstream(
    char* ptr);

istrstream(
    const char* ptr,
    streamsize count);

istrstream(
    char* ptr,
    int count);
```

### <a name="parameters"></a>매개 변수

*수*\
버퍼의 길이 (*ptr*)입니다.

*ptr*\
버퍼가 초기화되는 콘텐츠입니다.

### <a name="remarks"></a>설명

모든 생성자는 [istream](../standard-library/istream-typedefs.md#istream)(**sb**)을 호출 하 여 기본 클래스를 초기화 `sb` 합니다. 여기서은 [strstreambuf](../standard-library/strstreambuf-class.md)클래스의 저장 된 개체입니다. 처음 두 생성자는를 `sb` 호출 하 여도 초기화 `strstreambuf( ( const char *) ptr, 0 )` 합니다. 나머지 두 생성자는 대신를 호출 `strstreambuf( ( const char *) ptr, count )` 합니다.

## <a name="istrstreamrdbuf"></a><a name="rdbuf"></a> istrstream:: rdbuf

스트림의 연결된 strstreambuf 개체에 대한 포인터를 반환합니다.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>반환 값

스트림의 연결된 strstreambuf 개체에 대한 포인터입니다.

### <a name="remarks"></a>설명

멤버 함수는 pointer 형식의 저장된 스트림 버퍼 주소를 [strstreambuf](../standard-library/strstreambuf-class.md)에 반환합니다.

### <a name="example"></a>예제

`rdbuf`를 사용하는 샘플은 [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount)를 참조하세요.

## <a name="istrstreamstr"></a><a name="str"></a> istrstream:: str

[freeze](../standard-library/strstreambuf-class.md#freeze)를 호출한 다음 제어되는 시퀀스의 시작 부분에 대한 포인터를 반환합니다.

```cpp
char *str();
```

### <a name="return-value"></a>반환 값

제어되는 시퀀스의 시작 부분에 대한 포인터입니다.

### <a name="remarks"></a>설명

멤버 함수는 [rdbuf](#rdbuf)  ->  [str](../standard-library/strstreambuf-class.md#str)을 반환 합니다.

### <a name="example"></a>예제

를 사용 하는 샘플은 [strstream:: str](../standard-library/strstreambuf-class.md#str) 을 참조 하세요 `str` .

## <a name="see-also"></a>참고 항목

[istream](../standard-library/istream-typedefs.md#istream)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 프로그래밍](../standard-library/iostream-programming.md)\
[iostreams 규칙](../standard-library/iostreams-conventions.md)
