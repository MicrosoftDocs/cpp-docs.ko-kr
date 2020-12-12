---
description: '다음에 대 한 자세한 정보: &lt; filesystem &gt; 함수'
title: '&lt;filesystem&gt; 함수'
ms.date: 03/27/2019
f1_keywords:
- FILESYSTEM/std::experimental::filesystem::absolute
- FILESYSTEM/std::experimental::filesystem::canonical
- FILESYSTEM/std::experimental::filesystem::copy
- FILESYSTEM/std::experimental::filesystem::copy_file
- FILESYSTEM/std::experimental::filesystem::copy_symlink
- FILESYSTEM/std::experimental::filesystem::create_directories
- FILESYSTEM/std::experimental::filesystem::create_directory
- FILESYSTEM/std::experimental::filesystem::create_directory_symlink
- FILESYSTEM/std::experimental::filesystem::create_hard_link
- FILESYSTEM/std::experimental::filesystem::create_symlink
- FILESYSTEM/std::experimental::filesystem::current_path
- FILESYSTEM/std::experimental::filesystem::equivalent
- FILESYSTEM/std::experimental::filesystem::exists
- FILESYSTEM/std::experimental::filesystem::file_size
- FILESYSTEM/std::experimental::filesystem::hard_link_count
- FILESYSTEM/std::experimental::filesystem::hash_value
- FILESYSTEM/std::experimental::filesystem::is_block_file
- FILESYSTEM/std::experimental::filesystem::is_character_file
- FILESYSTEM/std::experimental::filesystem::is_directory
- FILESYSTEM/std::experimental::filesystem::is_empty
- FILESYSTEM/std::experimental::filesystem::is_fifo
- FILESYSTEM/std::experimental::filesystem::is_other
- FILESYSTEM/std::experimental::filesystem::is_regular_file
- FILESYSTEM/std::experimental::filesystem::is_socket
- FILESYSTEM/std::experimental::filesystem::is_symlink
- FILESYSTEM/std::experimental::filesystem::last_write_time
- FILESYSTEM/std::experimental::filesystem::permissions
- FILESYSTEM/std::experimental::filesystem::read_symlink
- FILESYSTEM/std::experimental::filesystem::remove
- FILESYSTEM/std::experimental::filesystem::remove_all
- FILESYSTEM/std::experimental::filesystem::rename
- FILESYSTEM/std::experimental::filesystem::resize_file
- FILESYSTEM/std::experimental::filesystem::space
- FILESYSTEM/std::experimental::filesystem::status
- FILESYSTEM/std::experimental::filesystem::status_known
- FILESYSTEM/std::experimental::filesystem::swap
- FILESYSTEM/std::experimental::filesystem::symlink_status
- FILESYSTEM/std::experimental::filesystem::system_complete
- FILESYSTEM/std::experimental::filesystem::temp_directory_path
- FILESYSTEM/std::experimental::filesystem::u8path
ms.assetid: be3cb821-4728-4d47-ab78-858fa8aa5045
helpviewer_keywords:
- std::experimental::filesystem::absolute
- std::experimental::filesystem::canonical
- std::experimental::filesystem::copy
- std::experimental::filesystem::copy_file
- std::experimental::filesystem::copy_symlink
- std::experimental::filesystem::create_directories
- std::experimental::filesystem::create_directory
- std::experimental::filesystem::create_directory_symlink
- std::experimental::filesystem::create_hard_link
- std::experimental::filesystem::create_symlink
- std::experimental::filesystem::current_path
- std::experimental::filesystem::equivalent
- std::experimental::filesystem::exists
- std::experimental::filesystem::file_size
- std::experimental::filesystem::hard_link_count
- std::experimental::filesystem::hash_value
- std::experimental::filesystem::is_block_file
- std::experimental::filesystem::is_character_file
- std::experimental::filesystem::is_directory
- std::experimental::filesystem::is_empty
- std::experimental::filesystem::is_fifo
- std::experimental::filesystem::is_other
- std::experimental::filesystem::is_regular_file
- std::experimental::filesystem::is_socket
- std::experimental::filesystem::is_symlink
- std::experimental::filesystem::last_write_time
- std::experimental::filesystem::permissions
- std::experimental::filesystem::read_symlink
- std::experimental::filesystem::remove
- std::experimental::filesystem::remove_all
- std::experimental::filesystem::rename
- std::experimental::filesystem::resize_file
- std::experimental::filesystem::space
- std::experimental::filesystem::status
- std::experimental::filesystem::status_known
- std::experimental::filesystem::swap
- std::experimental::filesystem::symlink_status
- std::experimental::filesystem::system_complete
- std::experimental::filesystem::temp_directory_path
- std::experimental::filesystem::u8path
ms.openlocfilehash: cb171228fe384a8f1269f52ab5905ed564818778
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324323"
---
# <a name="ltfilesystemgt-functions"></a>&lt;filesystem&gt; 함수

헤더의 이러한 free 함수 [\<filesystem>](../standard-library/filesystem.md) 는 경로, 파일, symlink, 디렉터리 및 볼륨에 대 한 수정 및 쿼리 작업을 수행 합니다. 자세한 내용 및 코드 예제는 [파일 시스템 탐색 (c + +)](../standard-library/file-system-navigation.md)을 참조 하세요.

## <a name="absolute"></a><a name="absolute"></a> 32x32

```cpp
path absolute(const path& pval, const path& base = current_path());
```

함수는 pathname을 기준으로 *pval* 에 해당 하는 절대 경로 이름을 반환 합니다 `base` .

1. `pval.has_root_name() && pval.has_root_directory()`함수에서 *pval* 를 반환 하는 경우입니다.

1. `pval.has_root_name() && !pval.has_root_directory()`함수가를 반환 하면 `pval.root_name()`  /  `absolute(base).root_directory()`  /  `absolute(base).relative_path()`  /  `pval.relative_path()` 입니다.

1. `!pval.has_root_name() && pval.has_root_directory()`함수에서 pval를 반환 하는 경우 `absolute(base).root_name()`  /  입니다.

1. `!pval.has_root_name() && !pval.has_root_directory()`함수에서 pval를 반환 하는 경우 `absolute(base)`  /  입니다.

## <a name="begin"></a><a name="begin"></a> begin

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

두 함수는 모두 *iter* 를 반환 합니다.

## <a name="canonical"></a><a name="canonical"></a> 전형적인

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

함수는 모두 절대 경로 이름 `pabs = absolute(pval, base)` (또는 `pabs = absolute(pval)` 기본 매개 변수가 없는 오버 로드의 경우)을 구성 하 고 다음 단계 시퀀스에서 정규 형식으로 줄입니다.

1. 가 인 모든 경로 구성 요소는 `X` `is_symlink(X)` **`true`** 로 대체 됩니다 `read_symlink(X)` .

1. 모든 경로 구성 요소 `.` (점이 이전 경로 구성 요소에서 설정한 현재 디렉터리)가 제거 됩니다.

1. 모든 경로 구성 요소 쌍 `X` / `..` (점-점은 이전 경로 구성 요소에서 설정한 부모 디렉터리)이 제거 됩니다.

그러면 함수는를 반환 `pabs` 합니다.

## <a name="copy"></a><a name="copy"></a> 복사

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

모든 함수는  opts 매개 변수가 없는 오버 로드에 대해으로 사용 되는 opts의 제어를 받는에서에 하나 이상의 파일을 복사 하거나 연결할 수 있습니다  `copy_options::none` .  *opts* 에는 다음 중 하나만 포함 되어야 합니다.

- `skip_existing`, `overwrite_existing`또는 `update_existing`

- `copy_symlinks` 또는 `skip_symlinks`

- `directories_only`, `create_symlinks` 또는 `create_hard_links`

함수는 먼저에서에 대 한 file_status 값을 확인 `f` 하 고,에 대해  `t` 다음 *을* 수행 합니다.

- 이면 `opts & (copy_options::create_symlinks | copy_options::skip_symlinks)` 를 호출 하 여 `symlink_status`

- 그렇지 않으면 다음을 호출 합니다. `status`

- 그렇지 않으면 오류를 보고합니다.

인 경우 `!exists(f) || equivalent(f, t) || is_other(f) || is_other(t) || is_directory(f)&& is_regular_file(t)` 오류를 보고 하 고 다른 작업은 수행 하지 않습니다.

그렇지 않으면 `is_symlink(f)` 다음을 수행 합니다.

- 이면 `options & copy_options::skip_symlinks` 아무 작업도 수행 하지 않습니다.

- 그렇지 않으면이 고, 그렇지 않으면 `!exists(t)&& options & copy_options::copy_symlinks` `copy_symlink(from, to, opts)` 입니다.

- 그렇지 않으면 오류를 보고 합니다.

그렇지 않으면이 고, 그렇지 않으면입니다 `is_regular_file(f)` .

- 이면 `opts & copy_options::directories_only` 아무 작업도 수행 하지 않습니다.

- 그렇지 않으면이 고, 그렇지 않으면 `opts & copy_options::create_symlinks` `create_symlink(to, from)` 입니다.

- 그렇지 않으면이 고, 그렇지 않으면 `opts & copy_options::create_hard_links` `create_hard_link(to, from)` 입니다.

- 그렇지 않으면이 고, 그렇지 않으면 `is_directory(f)` `copy_file(from, to`  /  `from.filename(), opts)` 입니다.

- 그렇지 않으면 `copy_file(from, to, opts)`입니다.

그렇지 않으면이 고, 그렇지 않으면입니다 `is_directory(f) && (opts & copy_options::recursive || !opts)` .

```cpp
if (!exists(t))
{  // copy directory contents recursively
    create_directory(to, from, ec);

    for (directory_iterator next(from), end; ec == error_code() && next != end; ++next)
    {
        copy(next->path(), to / next->path().filename(), opts, ec);
    }
}
```

그렇지 않으면 아무 작업도 수행하지 않습니다.

## <a name="copy_file"></a><a name="copy_file"></a> copy_file

```cpp
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

모든 함수는    `copy_options::none` *opts* 매개 변수가 없는 오버 로드에 대해 opts의 제어를 받는에서로의 파일을에 복사할 수 있습니다. *opts* 에는, 또는 중 하나만 포함 되어야 `skip_existing` `overwrite_existing` `update_existing` 합니다.

이면 `exists(to) && !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options::update_existing))` 파일이 이미 있다는 오류로 보고 합니다.

그렇지 않고, 인 경우 파일 `!exists(to) || opts & copy_options::overwrite_existing || opts & copy_options::update_existing&& last_write_time(to) < last_write_time(from) || !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options:update_existing))` 의 내용과 특성을 *에서* *로* 복사 하려고 시도 합니다. 복사 시도가 실패하는 경우 오류로 보고합니다.

**`true`** 복사를 시도 하 여 성공 하면 함수는를 반환 하 고 그렇지 않으면를 반환 **`false`** 합니다.

## <a name="copy_symlink"></a><a name="copy_symlink"></a> copy_symlink

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

이면 `is_directory(from)` 함수는를 호출 `create_directory_symlink(from, to)` 합니다. 그렇지 않으면 `create_symlink(from, to)`합니다.

## <a name="create_directories"></a><a name="create_directories"></a> create_directories

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

A b c와 같은 경로 이름에 대해 함수는 필요에 따라 \/ \/ \/ 디렉터리 a b c를 만들 수 있도록 필요에 따라 디렉터리 a 및 b를 만듭니다 \/ \/ . **`true`** 실제로 디렉터리 *pval* 을 만드는 경우에만를 반환 합니다.

## <a name="create_directory"></a><a name="create_directory"></a> create_directory

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

이 함수는 필요에 따라 *pval* 디렉터리를 만듭니다. 실제로 디렉터리 *pval* 을 만드는 경우에만 true를 반환 합니다 .이 경우 기존 파일 *특성* 에서 사용 권한을 복사 하거나 `perms::all` *특성* 매개 변수가 없는 오버 로드에 대해를 사용 합니다.

## <a name="create_directory_symlink"></a><a name="create_directory_symlink"></a> create_directory_symlink

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

함수는 디렉터리에 *대* 한 링크를 symlink로 만듭니다.

## <a name="create_hard_link"></a><a name="create_hard_link"></a> create_hard_link

```cpp
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;
```

함수는 디렉터리 또는 파일에 대 한 링크를 *에 대* 한 하드 링크로 만듭니다.

## <a name="create_symlink"></a><a name="create_symlink"></a> create_symlink

```cpp
void create_symlink(const path& to, const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

함수 *는 파일에 대 한* *링크* 를 symlink로 만듭니다.

## <a name="current_path"></a><a name="current_path"></a> current_path

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

*Pval* 매개 변수가 없는 함수는 현재 디렉터리에 대 한 경로 이름을 반환 합니다. 나머지 함수는 현재 디렉터리를 *pval* 로 설정 합니다.

## <a name="end"></a><a name="end"></a> end

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

첫 번째 함수는 `directory_iterator()` 를 반환 하 고 두 번째 함수는를 반환 합니다. `recursive_directory_iterator()`

## <a name="equivalent"></a><a name="equivalent"></a> 해당 항목

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

함수는 **`true`** *left* 및 *right* 가 동일한 파일 시스템 엔터티를 선택 하는 경우에만를 반환 합니다.

## <a name="exists"></a><a name="exists"></a> 있으면

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

첫 번째 함수는 `status_known && stat.type() != file_not_found`를 반환합니다. 두 번째 및 세 번째 함수는를 반환 합니다 `exists(status(pval))` .

## <a name="file_size"></a><a name="file_size"></a> file_size

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

함수는 *pval* 에서 선택한 파일의 크기 (바이트)를 반환 하며,이 경우 `exists(pval) && is_regular_file(pval)` 파일 크기를 확인할 수 있습니다. 그렇지 않으면 오류를 보고 하 고를 반환 `uintmax_t(-1)` 합니다.

## <a name="hard_link_count"></a><a name="hard_link_count"></a> hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

함수는 *pval* 에 대 한 하드 링크의 수를 반환 하거나, 오류가 발생 하는 경우 1을 반환 합니다 \- .

## <a name="hash_value"></a><a name="hash_value"></a> hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

함수는에 대 한 해시 값을 반환 합니다 `pval.native()` .

## <a name="is_block_file"></a><a name="is_block_file"></a> is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

첫 번째 함수는 `stat.type() == file_type::block`를 반환합니다. 나머지 함수는를 반환 `is_block_file(status(pval))` 합니다.

## <a name="is_character_file"></a><a name="is_character_file"></a> is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

첫 번째 함수는 `stat.type() == file_type::character`를 반환합니다. 나머지 함수는를 반환 `is_character_file(status(pval))` 합니다.

## <a name="is_directory"></a><a name="is_directory"></a> is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

첫 번째 함수는 `stat.type() == file_type::directory`를 반환합니다. 나머지 함수는를 반환 `is_directory_file(status(pval))` 합니다.

## <a name="is_empty"></a><a name="is_empty"></a> is_empty

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

이면 `is_directory(pval)` 함수는를 반환 하 `directory_iterator(pval) == directory_iterator()` 고, 그렇지 않으면를 반환 `file_size(pval) == 0` 합니다.

## <a name="is_fifo"></a><a name="is_fifo"></a> is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

첫 번째 함수는 `stat.type() == file_type::fifo`를 반환합니다. 나머지 함수는를 반환 `is_fifo(status(pval))` 합니다.

## <a name="is_other"></a><a name="is_other"></a> is_other

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

첫 번째 함수는 `stat.type() == file_type::other`를 반환합니다. 나머지 함수는를 반환 `is_other(status(pval))` 합니다.

## <a name="is_regular_file"></a><a name="is_regular_file"></a> is_regular_file

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

첫 번째 함수는 `stat.type() == file_type::regular`를 반환합니다. 나머지 함수는를 반환 `is_regular_file(status(pval))` 합니다.

## <a name="is_socket"></a><a name="is_socket"></a> is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

첫 번째 함수는 `stat.type() == file_type::socket`를 반환합니다. 나머지 함수는를 반환 `is_socket(status(pval))` 합니다.

## <a name="is_symlink"></a><a name="is_symlink"></a> is_symlink

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

첫 번째 함수는 `stat.type() == file_type::symlink`를 반환합니다. 나머지 함수는를 반환 `is_symlink(status(pval))` 합니다.

## <a name="last_write_time"></a><a name="last_write_time"></a> last_write_time

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

처음 두 함수는 *pval* 에 대 한 마지막 데이터 수정 시간을 반환 하거나 오류가 발생 하는 경우를 반환 합니다 `file_time_type(-1)` . 마지막 두 함수는 *pval* 에 대 한 마지막 데이터 수정 시간을 *new_time* 설정 합니다.

## <a name="permissions"></a><a name="permissions"></a> 권한에

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

함수는 *pval* 에서 선택한 경로 이름에 대 한 사용 권한을 `mask & perms::mask` 의 제어에서 설정 합니다 `perms & (perms::add_perms | perms::remove_perms)` . *mask* 에는 및 중 하나만 포함 `perms::add_perms` 되어야 `perms::remove_perms` 합니다.

인 경우 `mask & perms::add_perms` 함수는 사용 권한을로 설정 합니다 `status(pval).permissions() | mask & perms::mask` . 그렇지 않으면 `mask & perms::remove_perms` 함수는 사용 권한을로 설정 합니다 `status(pval).permissions() & ~(mask & perms::mask)` . 그렇지 않으면 함수는 사용 권한을로 설정 합니다 `mask & perms::mask` .

## <a name="proximate"></a><a name="proximate"></a> 가까이 있는

```cpp
path proximate(const path& p, error_code& ec);
path proximate(const path& p, const path& base = current_path());
path proximate(const path& p, const path& base, error_code& ec);
```

## <a name="read_symlink"></a><a name="read_symlink"></a> read_symlink

```cpp
path read_symlink(const path& pval);
path read_symlink(const path& pval, error_code& ec);
```

함수는 오류를 보고 하 고 `path()` 인 경우을 반환 `!is_symlink(pval)` 합니다. 그렇지 않은 경우 함수는 기호 링크를 포함하는 `path` 형식의 개체를 반환합니다.

## <a name="relative"></a><a name="relative"></a> 배분

```cpp
path relative(const path& p, error_code& ec);
path relative(const path& p, const path& base = current_path());
path relative(const path& p, const path& base, error_code& ec);
```

## <a name="remove"></a><a name="remove"></a> 삭제

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

함수는 **`true`** `exists(symlink_status(pval))` 및 파일이 성공적으로 제거 된 경우에만를 반환 합니다. Symlink은 자신이 선택 하는 파일이 아니라 자체적으로 제거 됩니다.

## <a name="remove_all"></a><a name="remove_all"></a> remove_all

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

*Pval* 가 디렉터리인 경우 함수는 모든 디렉터리 항목을 재귀적으로 제거한 다음 항목 자체를 제거 합니다. 그렇지 않으면 함수는를 호출 `remove` 합니다. 함수는 성공적으로 제거된 모든 요소의 수를 반환합니다.

## <a name="rename"></a><a name="rename"></a> 바꾸면

```cpp
void rename(const path& from, const path& to);
void rename(const path& from, const path& to, error_code& ec) noexcept;
```

함수는 *에서* 로의 이름을로 *바꿉니다.* Symlink은 자신이 선택 하는 파일이 아니라 이름이 변경 됩니다.

## <a name="resize_file"></a><a name="resize_file"></a> resize_file

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

함수는 파일 크기를 변경 합니다. `file_size(pval) == size`

## <a name="space"></a><a name="space"></a> 공간

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

함수는 *pval* 에 의해 선택 된 볼륨에 대 한 정보를 형식의 구조체로 반환 합니다 `space_info` . 구조에는 `uintmax_t(-1)` 확인할 수 없는 값이 포함 됩니다.

## <a name="status"></a><a name="status"></a> 업무

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

함수는 *pval* 와 연결 된 경로 이름 상태, 파일 형식 및 사용 권한을 반환 합니다. Symlink는 자체적으로 테스트 되지 않지만 선택 된 파일입니다.

## <a name="status_known"></a><a name="status_known"></a> status_known

```cpp
bool status_known(file_status stat) noexcept;
```

함수는를 반환 합니다. `stat.type() != file_type::none`

## <a name="swap"></a><a name="swap"></a> 스왑을

```cpp
void swap(path& left, path& right) noexcept;
```

함수는 *왼쪽과* *오른쪽* 의 내용을 교환 합니다.

## <a name="symlink_status"></a><a name="symlink_status"></a> symlink_status

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, error_code& ec) noexcept;
```

함수는 *pval* 과 관련 된 경로 이름 symlink 상태, 파일 형식 및 사용 권한을 반환 합니다. 함수는 `status(pval)` symlink가 선택 하는 파일이 아니라 테스트 자체를 테스트 한다는 점을 제외 하 고 동일 하 게 동작 합니다.

## <a name="system_complete"></a><a name="system_complete"></a> system_complete

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

이 함수는 필요에 따라 루트 이름과 연결된 현재 디렉터리를 고려하는 절대 경로 이름을 반환합니다. \(POSIX의 경우 함수는를 반환 `absolute(pval)` 합니다.\)

## <a name="temp_directory_path"></a><a name="temp_directory_path"></a> temp_directory_path

```cpp
path temp_directory_path();
path temp_directory_path(error_code& ec);
```

이 함수는 임시 파일을 포함하는 데 적합한 디렉터리의 경로 이름을 반환합니다.

## <a name="u8path"></a><a name="u8path"></a> u8path

```cpp
template <class Source>
path u8path(const Source& source);

template <class InIt>
path u8path(InIt first, InIt last);
```

첫 번째 함수는와 동일 하 게 작동 `path(source)` 하며, 두 번째 함수는 `path(first, last)` 각 사례에서 선택 된 소스가 u t f-8로 인코드된 char 요소의 시퀀스로 사용 되는 것과 동일 하 게 동작 합니다. 단, 파일 시스템에는 무엇이 든 상관 없습니다.

## <a name="weakly_canonical"></a><a name="weakly_canonical"></a> weakly_canonical

```cpp
path weakly_canonical(const path& p);
path weakly_canonical(const path& p, error_code& ec);
```
