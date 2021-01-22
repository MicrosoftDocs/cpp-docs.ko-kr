---
title: '&lt;filesystem&gt;'
description: filesystem표준 c + + 라이브러리 헤더의 클래스, 함수 및 형식을 설명 합니다.
ms.date: 01/15/2021
f1_keywords:
- <filesystem>
- filesystem/std::filesystem
- std::filesystem
- std::experimental::filesystem
no-loc:
- filesystem
- experimental
- char
- wchar_t
- char16_t
- char32_t
ms.openlocfilehash: 8dc81692c7c7dc467f3ab8e2ceb8cac19e004ab8
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98667468"
---
# `filesystem`

`<filesystem>`경로, 파일 및 디렉터리에 대 한 정보를 조작 하 고 검색 하는 클래스 및 함수에 대 한 액세스를 위한 헤더를 포함 합니다.

## <a name="syntax"></a>Syntax

```cpp
#include <filesystem> // C++17 standard header file name
#include <experimental/filesystem> // Header file for pre-standard implementation
using namespace std::experimental::filesystem::v1;
```

> [!IMPORTANT]
> Visual Studio 2017의 릴리스에서 \<filesystem> 헤더는 아직 c + + 표준이 아닙니다. Visual Studio의 c + + 2017 RTW는 [ISO/IEC JTC 1/SC 22/WG 21 N4100](https://wg21.link/n4100)에 있는 최종 초안 표준을 구현 합니다. Visual Studio 2017 버전 15.7 이상에서는 새로운 c + + 17 \<filesystem> 표준을 지원 합니다.
> 이것은 이전 버전과 호환 되지 않는 완전히 새로운 구현입니다 `std::experimental` . Symlink 지원, 버그 수정 및 표준 필수 동작의 변경에 의해 필요 했습니다. 현재를 포함 하는는 \<filesystem> 새 및 이전를 제공 합니다 `std::filesystem` `std::experimental::filesystem` . 포함 \<experimental/filesystem> 은 이전 구현만 제공 experimental 합니다. experimental구현은 다음 ABI 분리 라이브러리 릴리스에서 제거 될 예정입니다.

이 헤더는 Microsoft Windows 및 POSIX의 광범위 한 두 호스트 운영 체제 클래스 중 하나에 대 한 파일 시스템을 지원 합니다.

대부분의 기능이 두 운영 체제에서 공통되지만 이 문서에서는 차이가 있는 위치를 식별합니다. 다음은 그 예입니다. 

- Windows는 또는와 같은 여러 루트 이름을 `c:` 지원 `\\network_name` 합니다. 파일 시스템은 트리의 포리스트로 구성 되며, 각각에는 고유한 루트 디렉터리 (예: 또는) `c:\` 가 `\\network_name\` 있으며 상대 경로 이름 (절대 경로 이름 아님)을 완료 하는 데 고유한 현재 디렉터리가 있습니다.

- POSIX는 루트 이름이 없고 단일 루트 디렉터리와 단일 현재 디렉터리가 있는 단일 트리를 지원 `/` 합니다.

또 다른 중요한 차이점은 경로 이름의 기본 표시입니다.

- Windows에서는 **`wchar_t`** u t f-16으로 인코딩된의 null로 끝나는 시퀀스를 사용 합니다 (각 acter에 대해 하나 이상의 요소 char ).

- POSIX는 **`char`** u t f-8로 인코딩된의 null로 끝나는 시퀀스를 사용 합니다 (각 acter에 대해 하나 이상의 요소 char ).

- 클래스의 개체는 `path` 경로 이름을 네이티브 형식으로 저장 하지만이 저장 된 형식과 여러 외부 양식 간의 쉬운 변환을 지원 합니다.

  - 운영 체제에서 선호 하는 대로 인코딩된의 null로 끝나는 시퀀스입니다 **`char`** .

  - **`char`** U t f-8로 인코딩된의 null로 끝나는 시퀀스입니다.

  - 운영 체제에서 선호 하는 대로 인코딩된의 null로 끝나는 시퀀스입니다 **`wchar_t`** .

  - **`char16_t`** U t f-16으로 인코딩된의 null로 끝나는 시퀀스입니다.

  - **`char32_t`** U t f-32로 인코딩된의 null로 끝나는 시퀀스입니다.

  이러한 표시 간의 상호 변환은 하나 이상의 `codecvt` 패싯을 사용하여 필요에 따라 조정됩니다. 특정 로캘 개체를 지정 하지 않으면 전역 로캘에서 이러한 패싯을 가져옵니다.

또 다른 차이점은 각 운영 체제에서 파일 또는 디렉터리 액세스 권한을 지정할 수 있는 세부 정보입니다.

- Windows는 파일이 읽기 전용인 지 쓰기 가능한 지, 디렉터리에 대 한 의미가 없는 특성을 기록 합니다.

- POSIX는 파일이 읽기, 쓰기 또는 실행 (디렉터리의 경우) 될 수 있는지 여부를 기록 합니다. 또한 각 작업이 소유자, 소유자 그룹 또는 모든 사람에 대해 허용 되는지 여부와 몇 가지 다른 사용 권한이 있습니다.

두 시스템에 공통되는 점은 루트 이름을 통과할 경우 경로 이름에 적용되는 구조입니다. 경로 이름 `c:/abc/xyz/def.ext` :

- 루트 이름은 `c:` 입니다.

- 루트 디렉터리는 `/` 입니다.

- 루트 `c:/` 경로가 인 경우

- 상대 경로는 `abc/xyz/def.ext` 입니다.

- 부모 `c:/abc/xyz` 경로가 인 경우

- 파일 이름이 `def.ext`인 경우

- 스템는 `def` 입니다.

- 확장이 `.ext` 인 경우

사소한 차이점은 경로 이름에서 디렉터리 시퀀스 사이의 기본 구분 기호입니다. 두 운영 체제에서 슬래시를 작성할 수 `/` 있지만 일부 컨텍스트에서 Windows는 백슬래시를 선호 `\` 합니다. 구현은의 데이터 멤버에 기본 설정 구분 기호를 `preferred_separator` 저장 `path` 합니다.

마지막으로 `path` 개체는 중요 한 기능을 포함 합니다. 헤더에 정의 된 클래스에서 filename 인수가 필요한 모든 위치에서 개체를 사용할 수 있습니다 [\<fstream>](fstream.md) .

자세한 내용 및 코드 예제는 [파일 시스템 탐색 (c + +)](../standard-library/file-system-navigation.md)을 참조 하세요.

## <a name="members"></a>멤버

### <a name="classes"></a>클래스

|이름|Description|
|-|-|
|[`directory_entry` 클래스](../standard-library/directory-entry-class.md)|또는에 의해 반환 되 `directory_iterator` `recursive_directory_iterator` 고를 포함 하는 개체를 설명 합니다 `path` .|
|[`directory_iterator` 클래스](../standard-library/directory-iterator-class.md)|파일 시스템 디렉터리에서 파일 이름을 통해 시퀀스되는 입력 반복기에 대해 설명합니다.|
|[`filesystem_error` 클래스](../standard-library/filesystem-error-class.md)|하위 수준 시스템 오버플로를 보고하기 위해 throw되는 예외에 대한 기본 클래스입니다.|
|[`path` 클래스](../standard-library/path-class.md)|파일 이름으로 사용하기 적합한 템플릿 형식 `String` 의 개체를 저장하는 클래스를 정의합니다.|
|[`recursive_directory_iterator` 클래스](../standard-library/recursive-directory-iterator-class.md)|파일 시스템 디렉터리에서 파일 이름을 통해 시퀀스되는 입력 반복기에 대해 설명합니다. 이 반복기는 하위 디렉터리로도 상속됩니다.|
|[`file_status` 클래스](../standard-library/file-status-class.md)|`file_type`을 래핑합니다.|

### <a name="structs"></a>구조체

|속성|Description|
|-|-|
|[`space_info` 구조체나](../standard-library/space-info-structure.md)|볼륨에 대한 정보를 보관합니다.|

## <a name="functions"></a>Functions

[\<filesystem> 역함수](../standard-library/filesystem-functions.md)

## <a name="operators"></a>연산자

[\<filesystem> 작업자](../standard-library/filesystem-operators.md)

## <a name="enumerations"></a>열거형

|속성|Description|
|-|-|
|[`copy_options`](../standard-library/filesystem-enumerations.md#copy_options)|[copy_file](../standard-library/filesystem-functions.md#copy_file) 과 함께 사용되는 열거형이며 대상 파일이 이미 있는 경우의 동작을 결정합니다.|
|[`directory_options`](../standard-library/filesystem-enumerations.md#directory_options)|디렉터리 반복기에 대한 옵션을 지정하는 열거형입니다.|
|[`file_type`](../standard-library/filesystem-enumerations.md#file_type)|파일 형식에 대한 열거형입니다.|
|[`perm_options`](../standard-library/filesystem-enumerations.md#perm_options)| 함수에 대 한 옵션을 열거 `permissions` 합니다. |
|[`perms`](../standard-library/filesystem-enumerations.md#perms)|사용 권한 및 사용 권한에 대한 옵션을 전달하는 데 사용되는 비트 마스크 형식입니다.|

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)
