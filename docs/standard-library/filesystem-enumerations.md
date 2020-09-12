---
title: '&lt;filesystem&gt; 열거형'
ms.date: 11/04/2016
f1_keywords:
- filesystem/std::filesystem::copy_options
- filesystem/std::experimental::filesystem::copy_options
- filesystem/std::filesystem::directory_options
- filesystem/std::experimental::filesystem::directory_options
- filesystem/std::filesystem::file_type
- filesystem/std::experimental::filesystem::file_type
- filesystem/std::filesystem::perms
- filesystem/std::experimental::filesystem::perms
ms.assetid: 0096c046-d101-464c-8259-b878a48280b0
ms.openlocfilehash: 3c94ec899f0ea7abf71530f6aca44638fdb216c9
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041941"
---
# <a name="ltfilesystemgt-enumerations"></a>&lt;filesystem&gt; 열거형

이 항목에서는 filesystem 헤더의 열거형을 설명합니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<experimental/filesystem>

**네임스페이스:** std::experimental::filesystem

## <a name="copy_options"></a><a name="copy_options"></a> copy_options

동작을 지정하기 위해 [copy](filesystem-functions.md#copy) 및 [copy_file](filesystem-functions.md#copy_file) 함수와 함께 사용되는 비트 마스크 값의 열거형입니다.

### <a name="syntax"></a>구문

```cpp
enum class copy_options {
   none = 0,
   skip_existing = 1,
   overwrite_existing = 2,
   update_existing = 4,
   recursive = 8,
   copy_symlinks = 16,
   skip_symlinks = 32,
   directories_only = 64,
   create_symlinks = 128,
   create_hard_links = 256
};
```

### <a name="values"></a>값

| Name | Description |
|------------|-----------------|
|`none`|작업의 기본 동작을 수행합니다.|
|`skip_existing`|파일이 이미 있는 경우 복사하지 않고 오류를 보고하지 않습니다.|
|`overwrite_existing`|파일이 이미 있는 경우 덮어씁니다.|
|`update_existing`|파일이 이미 있고 대체 파일보다 오래된 경우 파일을 덮어씁니다.|
|`recursive`|하위 디렉터리와 해당 콘텐츠를 재귀적으로 복사합니다.|
|`copy_symlinks`|기호 링크가 가리키는 파일을 복사하지 않고 기호 링크를 기호 링크로 복사합니다.|
|`skip_symlinks`|기호 링크를 무시합니다.|
|`directories_only`|디렉터리만 반복하고 파일을 무시합니다.|
|`create_symlinks`|파일을 복사하지 않고 기호 링크를 만듭니다. 대상이 현재 디렉터리가 아니면 절대 경로를 소스 경로로 사용해야 합니다.|
|`create_hard_links`|파일을 복사하지 않고 하드 링크를 만듭니다.|

## <a name="directory_options"></a><a name="directory_options"></a> directory_options

디렉터리에 대한 기호화된 링크를 따를지, 아니면 무시할지 지정합니다.

### <a name="syntax"></a>구문

```cpp
enum class directory_options {
   none = 0,
   follow_directory_symlink
};
```

### <a name="values"></a>값

|Name|Description|
|----------|-----------------|
|`none`|기본 동작: 디렉터리에 대한 기호 링크를 무시합니다. 사용 권한이 거부됨은 오류입니다.|
|`follow_directory_symlink`|디렉터리에 대한 기호화된 링크를 실제 디렉터리로 처리합니다.|

## <a name="file_type"></a><a name="file_type"></a> file_type

파일 형식에 대한 열거형입니다. 지원 되는 값은 regular, directory, not_found 및 unknown입니다.

### <a name="syntax"></a>구문

```cpp
enum class file_type {
    not_found = -1,
    none,
    regular,
    directory,
    symlink,
    block,
    character,
    fifo,
    socket,
    unknown
};
```

### <a name="values"></a>값

|Name|값|Description|
|----------|-----------|-----------------|
|`not_found`|-1|존재하지 않는 파일을 나타냅니다.|
|`none`|0|형식 특성이 없는 파일을 나타냅니다. (지원 안 됨)|
|`regular`|1|기존 디스크 파일을 나타냅니다.|
|`directory`|2|디렉터리를 나타냅니다.|
|`symlink`|3|기호화된 링크를 나타냅니다. (지원 안 됨)|
|`block`|4|UNIX 기반 시스템의 블록 특수 파일을 나타냅니다. (지원 안 됨)|
|`character`|5|UNIX 기반 시스템의 문자 특수 파일을 나타냅니다. (지원 안 됨)|
|`fifo`|6|UNIX 기반 시스템의 FIFO 파일을 나타냅니다. (지원 안 됨)|
|`socket`|7|UNIX 기반 시스템의 소켓을 나타냅니다. (지원 안 됨)|
|`unknown`|8|해당 상태를 확인할 수 없는 파일을 나타냅니다.|

## <a name="perm_options"></a><a name="perm_options"></a> perm_options

에는,, 및 값이 포함 됩니다 `replace` `add` `remove` `nofollow` .

```cpp
enum class perm_options;
```

## <a name="perms"></a><a name="perms"></a> perms

파일 사용 권한에 대한 플래그입니다. 지원 되는 값은 기본적으로 "readonly" 및 all입니다. 읽기 전용 파일의 경우 *_write 비트가 설정되지 않습니다. 그렇지 않은 경우에는 `all` 비트(0x0777)가 설정됩니다.

### <a name="syntax"></a>구문

```cpp
enum class perms {// names for permissions
   none = 0,
   owner_read = 0400,  // S_IRUSR
   owner_write = 0200, // S_IWUSR
   owner_exec = 0100,  // S_IXUSR
   owner_all = 0700,   // S_IRWXU
   group_read = 040,   // S_IRGRP
   group_write = 020,  // S_IWGRP
   group_exec = 010,   // S_IXGRP
   group_all = 070,    // S_IRWXG
   others_read = 04,   // S_IROTH
   others_write = 02,  // S_IWOTH
   others_exec = 01,   // S_IXOTH
   others_all = 07,    // S_IRWXO
   all = 0777,
   set_uid = 04000,    // S_ISUID
   set_gid = 02000,    // S_ISGID
   sticky_bit = 01000, // S_ISVTX
   mask = 07777,
   unknown = 0xFFFF,
   add_perms = 0x10000,
   remove_perms = 0x20000,
   resolve_symlinks = 0x40000
};
```

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)
