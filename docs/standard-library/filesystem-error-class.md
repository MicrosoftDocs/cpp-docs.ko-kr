---
description: Filesystem_error 클래스에 대해 자세히 알아보세요.
title: filesystem_error 클래스
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
ms.openlocfilehash: 8165bfbc0d59dbbdab17d910e2e2f7973988049d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232436"
---
# <a name="filesystem_error-class"></a>filesystem_error 클래스

하위 수준 시스템 오버플로를 보고하기 위해 throw되는 모든 예외에 대한 기본 클래스입니다.

## <a name="syntax"></a>구문

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>설명

클래스는 함수에서 오류를 보고 하기 위해 throw 되는 모든 예외에 대 한 기본 클래스로 사용 \<filesystem> 됩니다. `string`표시의 목적으로 여기에 해당 하는 형식의 개체를 저장 `mymesg` 합니다. 또한 및 이라는 두 가지 형식의 개체 `path` 를 저장 `mypval1` `mypval2` 합니다.

## <a name="members"></a>멤버

### <a name="constructors"></a>생성자

|속성|설명|
|-|-|
|[filesystem_error](#filesystem_error)|메시지를 생성 `filesystem_error` 합니다.|

### <a name="functions"></a>함수

|Name|설명|
|-|-|
|[path1](#path1)|`mypval1`를 반환합니다.|
|[path2](#path2)|`mypval2`를 반환합니다.|
|[이며](#what)|`NTBS`에 대한 포인터를 반환합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<filesystem>

**네임스페이스:** std::experimental::filesystem

## <a name="filesystem_error"></a><a name="filesystem_error"></a> filesystem_error

첫 번째 생성자는 *what_arg* 와 *ec* 에서 메시지를 생성 합니다. 또한 두 번째 생성자는 *pval1* 에서 해당 메시지를 생성 하 여에 저장 `mypval1` 합니다. 세 번째 생성자는 *pval1* 에서 해당 메시지를 생성 하 고에 저장 되는 pval1에서 해당 메시지를 생성 `mypval1`  `mypval2` 합니다.

```cpp
filesystem_error(const string& what_arg,
    error_code ec);

filesystem_error(const string& what_arg,
    const path& pval1,
    error_code ec);

filesystem_error(const string& what_arg,
    const path& pval1,
    const path& pval2,
    error_code ec);
```

### <a name="parameters"></a>매개 변수

*what_arg*\
지정 된 메시지입니다.

*ec*\
지정 된 오류 코드입니다.

*mypval1*\
지정 된 추가 메시지 매개 변수입니다.

*mypval2*\
지정 된 추가 메시지 매개 변수입니다.

## <a name="path1"></a><a name="path1"></a> path1

구성원 함수는 `mypval1`을 반환합니다.

```cpp
const path& path1() const noexcept;
```

## <a name="path2"></a><a name="path2"></a> path2

구성원 함수는 `mypval2`을 반환합니다.

```cpp
const path& path2() const noexcept;
```

## <a name="what"></a><a name="what"></a> 이며

멤버 함수는,,, `NTBS` 및에서 구성 된에 대 한 포인터를 반환 합니다 `runtime_error::what()` `system_error::what()` `mymesg` `mypval1.native_string()` `mypval2.native_string()` .

```cpp
const char *what() const noexcept;
```
