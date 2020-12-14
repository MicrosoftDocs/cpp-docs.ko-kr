---
description: Directory_iterator 클래스에 대해 자세히 알아보세요.
title: directory_iterator 클래스
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::directory_iterator
- filesystem/std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator::directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator::increment
- filesystem/std::experimental::filesystem::directory_iterator::operator=
- filesystem/std::experimental::filesystem::directory_iterator::operator==
- filesystem/std::experimental::filesystem::directory_iterator::operator!=
- filesystem/std::experimental::filesystem::directory_iterator::operator*
- filesystem/std::experimental::filesystem::directory_iterator::operator-&gt;
- filesystem/std::experimental::filesystem::directory_iterator::operator++
ms.assetid: dca2ecf8-3e69-4644-a83d-705061e10cc8
helpviewer_keywords:
- std::experimental::filesystem::directory_iterator
- std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- std::experimental::filesystem::directory_iterator
- std::experimental::filesystem::directory_iterator::directory_iterator
- std::experimental::filesystem::directory_iterator::increment
- std::experimental::filesystem::directory_iterator::operator=
- std::experimental::filesystem::directory_iterator::operator==
- std::experimental::filesystem::directory_iterator::operator!=
- std::experimental::filesystem::directory_iterator::operator*
- std::experimental::filesystem::directory_iterator::operator-&gt;
- std::experimental::filesystem::directory_iterator::operator++
ms.openlocfilehash: 1bc0ac1d2d7816986bca1f48a41316270e547834
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232787"
---
# <a name="directory_iterator-class"></a>directory_iterator 클래스

디렉터리에서 파일 이름을 통해 시퀀스되는 입력 반복기에 대해 설명합니다. 반복기의 경우 `X` 식은 `*X` `directory_entry` 파일 이름 및 상태에 대해 알려진 모든 항목을 래핑하는 클래스의 개체로 계산 됩니다.

이 클래스는 표시의 목적을 위해 여기에 호출 되는 형식의 개체를 저장 합니다 .이 개체는 `path` `mydir` 시퀀싱 할 디렉터리의 이름을 나타내고 여기에서 호출 된 형식의 개체는 `directory_entry` `myentry` 디렉터리 시퀀스의 현재 파일 이름을 나타냅니다. 형식의 기본 생성 된 개체는 `directory_entry` 빈 `mydir` 경로 이름을 가지 며 시퀀스의 끝 반복기를 나타냅니다.

예를 들어, 및 항목을 포함 하는 디렉터리를 지정 하는 경우 `abc` `def` `ghi` 코드는 다음과 같습니다.

`for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`

는 `visit` 및 인수를 사용 하 여를 호출 합니다 `path("abc/def")` `path("abc/ghi")` .

자세한 내용 및 코드 예제는 [파일 시스템 탐색 (c + +)](../standard-library/file-system-navigation.md)을 참조 하세요.

## <a name="syntax"></a>Syntax

```cpp
class directory_iterator;
```

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[directory_iterator](#directory_iterator)|디렉터리의 파일 이름을 통해 시퀀스 되는 입력 반복기를 생성 합니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[increment](#increment)|디렉터리의 다음 파일 이름으로 이동 하려고 합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[연산자! =](#op_neq)|`!(*this == right)`를 반환합니다.|
|[연산자 =](#op_as)|기본 멤버 대입 연산자가 예상대로 작동합니다.|
|[연산자 = =](#op_eq)|**`true`** **`*this`** 와 *right* 가 둘 다 시퀀스의 끝 반복기 이거나 둘 다 시퀀스의 끝 반복기가 아닌 경우에만를 반환 합니다.|
|[연산자](#op_star)|`myentry`를 반환합니다.|
|[연산자->](#op_cast)|`&**this`를 반환합니다.|
|[operator + +](#op_increment)|는를 호출 `increment()` 하 여 개체의 복사본을 반환 하 고를 **`*this`** 호출한 `increment()` 다음 복사본을 반환 합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<experimental/filesystem>

**네임스페이스:** std::experimental::filesystem

## <a name="directory_iteratordirectory_iterator"></a><a name="directory_iterator"></a> directory_iterator::d irectory_iterator

첫 번째 생성자는 시퀀스의 끝 반복기를 생성합니다. 두 번째 및 세 번째 생성자는 *pval* 에를 저장 `mydir` 한 다음 디렉터리로 열고 읽으려고 시도 합니다 `mydir` . 성공 하면 첫 번째 파일 이름을의 디렉터리에 저장 하 `myentry` 고, 그렇지 않으면 시퀀스의 끝 반복기를 생성 합니다.

기본 생성자는 예상대로 작동합니다.

```cpp
directory_iterator() noexcept;
explicit directory_iterator(const path& pval);

directory_iterator(const path& pval, error_code& ec) noexcept;
directory_iterator(const directory_iterator&) = default;
directory_iterator(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>매개 변수

*pval*\
저장 된 파일 이름 경로입니다.

*ec*\
상태 오류 코드입니다.

*directory_iterator*\
저장 된 개체입니다.

## <a name="directory_iteratorincrement"></a><a name="increment"></a> directory_iterator:: 증가값

함수는 디렉터리의 다음 파일 이름으로 이동하려고 합니다. 성공 하면 해당 파일 이름을에 저장 하 `myentry` 고, 그렇지 않으면 시퀀스의 끝 반복기를 생성 합니다.

```cpp
directory_iterator& increment(error_code& ec) noexcept;
```

## <a name="directory_iteratoroperator"></a><a name="op_neq"></a> directory_iterator:: operator! =

멤버 연산자는 `!(*this == right)`를 반환합니다.

```cpp
bool operator!=(const directory_iterator& right) const;
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
`directory_iterator`와 비교할 [directory_iterator](../standard-library/directory-iterator-class.md)입니다.

## <a name="directory_iteratoroperator"></a><a name="op_as"></a> directory_iterator:: operator =

기본 멤버 대입 연산자가 예상대로 작동합니다.

```cpp
directory_iterator& operator=(const directory_iterator&) = default;
directory_iterator& operator=(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
`directory_iterator`에 복사되는 [directory_iterator](../standard-library/directory-iterator-class.md)입니다.

## <a name="directory_iteratoroperator"></a><a name="op_eq"></a> directory_iterator:: operator = =

멤버 연산자는 **`true`** **`*this`** 및 *권한이* 모두 시퀀스의 끝 반복기 이거나 둘 다 시퀀스의 끝 반복기가 아닌 경우에만를 반환 합니다.

```cpp
bool operator==(const directory_iterator& right) const;
```

### <a name="parameters"></a>매개 변수

*오른쪽*\
`directory_iterator`와 비교할 [directory_iterator](../standard-library/directory-iterator-class.md)입니다.

## <a name="directory_iteratoroperator"></a><a name="op_star"></a> directory_iterator:: operator *

멤버 연산자는 `myentry`를 반환합니다.

```cpp
const directory_entry& operator*() const;
```

## <a name="directory_iteratoroperator-"></a><a name="op_cast"></a> directory_iterator:: operator->

멤버 함수는 `&**this`를 반환합니다.

```cpp
const directory_entry * operator->() const;
```

## <a name="directory_iteratoroperator"></a><a name="op_increment"></a> directory_iterator:: operator + +

첫 번째 멤버 함수는 `increment()` 를 호출한 다음을 반환 **`*this`** 합니다. 두 번째 멤버 함수는 개체의 복사본을 만들고를 호출한 `increment()` 다음 복사본을 반환 합니다.

```cpp
directory_iterator& operator++();
directory_iterator& operator++(int);
```

### <a name="parameters"></a>매개 변수

*int*\
증가값입니다.

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[파일 시스템 탐색(C++)](../standard-library/file-system-navigation.md)
