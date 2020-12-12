---
description: File_status 클래스에 대해 자세히 알아보세요.
title: file_status 클래스
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::file_status
- filesystem/std::experimental::filesystem::file_status::operator=
- filesystem/std::experimental::filesystem::file_status::type
- filesystem/std::experimental::filesystem::file_status::permissions
ms.assetid: 9781840e-ad22-44dd-ad79-0fabaa94bac4
helpviewer_keywords:
- std::experimental::filesystem::file_status
- std::experimental::filesystem::file_status::operator=
- std::experimental::filesystem::file_status::type
- std::experimental::filesystem::file_status::permissions
ms.openlocfilehash: 8bc789d97f9b90b18214407fadab19e9644012a1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324366"
---
# <a name="file_status-class"></a>file_status 클래스

[file_type](../standard-library/filesystem-enumerations.md#file_type) 및 파일 [perms](../standard-library/filesystem-enumerations.md#perms)를 래핑합니다.

## <a name="syntax"></a>Syntax

```cpp
class file_status;
```

### <a name="constructors"></a>생성자

|생성자|Description|
|-|-|
|[file_status](#file_status)|[File_type](../standard-library/filesystem-enumerations.md#file_type) 및 파일 [perms](../standard-library/filesystem-enumerations.md#perms)에 대 한 래퍼를 생성 합니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|Description|
|-|-|
|[type](#type)|`file_type`를 가져오거나 설정합니다.|
|[사용 권한](#permissions)|파일 사용 권한을 가져오거나 설정합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[연산자 =](#op_as)|기본 멤버 대입 연산자가 예상대로 작동합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<filesystem>

**네임 스페이스:** std:: 실험적:: filesystem, std:: 실험적:: filesystem

## <a name="file_statusfile_status"></a><a name="file_status"></a> file_status:: file_status

[File_type](../standard-library/filesystem-enumerations.md#file_type) 및 파일 [perms](../standard-library/filesystem-enumerations.md#perms)에 대 한 래퍼를 생성 합니다.

```cpp
explicit file_status(
   file_type ftype = file_type::none,
   perms mask = perms::unknown) noexcept;

file_status(const file_status&) noexcept = default;

file_status(file_status&&) noexcept = default;

~file_status() noexcept = default;
```

### <a name="parameters"></a>매개 변수

*ftype*\
지정 된 `file_type` 경우 기본값은 `file_type::none` 입니다.

*마스크할*\
지정 된 파일 `perms` 의 기본값은 `perms::unknown` 입니다.

*file_status*\
저장 된 개체입니다.

## <a name="file_statusoperator"></a><a name="op_as"></a> file_status:: operator =

기본 멤버 대입 연산자가 예상대로 작동합니다.

```cpp
file_status& operator=(const file_status&) noexcept = default;
file_status& operator=(file_status&&) nexcept = default;
```

### <a name="parameters"></a>매개 변수

*file_status*\
`file_status`에 복사되는 [file_status](../standard-library/file-status-class.md)입니다.

## <a name="type"></a><a name="type"></a> 형식

`file_type`를 가져오거나 설정합니다.

```cpp
file_type type() const noexcept
void type(file_type ftype) noexcept
```

### <a name="parameters"></a>매개 변수

*ftype*\
`file_type`로 지정됩니다.

## <a name="permissions"></a><a name="permissions"></a> 권한에

파일 사용 권한을 가져오거나 설정합니다.

Setter를 사용 하 여 파일을 `readonly` 만들거나 특성을 제거 `readonly` 합니다.

```cpp
perms permissions() const noexcept
void permissions(perms mask) noexcept
```

### <a name="parameters"></a>매개 변수

*마스크할*\
`perms`로 지정됩니다.

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[path 클래스](../standard-library/path-class.md)\
[\<filesystem>](../standard-library/filesystem.md)
