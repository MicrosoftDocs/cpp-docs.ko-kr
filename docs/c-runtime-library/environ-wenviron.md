---
description: '자세히 알아보기: _environ, _wenviron'
title: _environ, _wenviron
ms.date: 11/04/2016
f1_keywords:
- environ
- wenviron
- _wenviron
- _environ
helpviewer_keywords:
- environ function
- _environ function
- _wenviron function
- process environment
- wenviron function
ms.assetid: 7e639962-6536-47cd-8095-0cbe44a56e03
ms.openlocfilehash: e1a69bec6fa93373c74e1f73de469bc3b93158e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305054"
---
# <a name="_environ-_wenviron"></a>_environ, _wenviron

`_environ` 변수는 프로세스 환경을 구성하는 멀티바이트 문자열에 대한 포인터 배열의 포인터입니다. 이 전역 변수는 전역 변수 대신 사용되어야 할 보안 기능이 보다 강화된 버전인 [getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md) 및 [_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)에 대해서는 더 이상 사용되지 않습니다. `_environ`은 Stdlib.h에서 선언됩니다.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.

## <a name="syntax"></a>구문

```
extern char **_environ;
```

## <a name="remarks"></a>설명

`main` 함수를 사용하는 프로그램에서 `_environ`은 프로그램 시작 시 운영 체제 환경에서 가져온 설정에 따라 초기화됩니다. 환경은 폼의 하나 이상의 항목으로 구성됩니다.

`ENVVARNAME` `=string`

`getenv_s` 및 `putenv_s`는 `_environ` 변수를 사용하여 환경 테이블에 액세스하고 테이블을 수정합니다. 환경 설정을 추가하거나 삭제하기 위해 `_putenv`가 호출되면 환경 테이블 크기가 변경됩니다. 프로그램의 메모리 요구 사항에 따라, 테이블의 메모리 내 위치도 변경될 수 있습니다. 이에 따라 `_environ`의 값이 자동으로 조정됩니다.

Stdlib.h에서 다음과 같이 선언되는 `_wenviron` 변수는

```
extern wchar_t **_wenviron;
```

와이드 문자 버전의 `_environ`입니다. `wmain` 함수를 사용하는 프로그램에서 `_wenviron`은 프로그램 시작 시 운영 체제 환경에서 가져온 설정에 따라 초기화됩니다.

환경이 멀티바이트 문자열로 구성되기 때문에, `main`을 사용하는 프로그램에서 `_wenviron`은 처음에 **NULL** 입니다. `_wgetenv` 또는 `_wputenv`에 대한 첫 번째 호출에서 해당하는 와이드 문자열 환경이 만들어지며 `_wenviron`이 이 환경을 가리킵니다.

마찬가지로, `wmain`을 사용하는 프로그램에서 환경이 와이드 문자열로 구성되기 때문에 `_environ`은 처음에 **NULL** 입니다. `_getenv` 또는 `_putenv`에 대한 첫 번째 호출에서 해당하는 멀티바이트 문자열 환경이 만들어지며 `_environ`이 이 환경을 가리킵니다.

환경의 두 개의 복사본(MBCS 및 유니코드)이 프로그램에 동시에 존재하는 경우 런타임 시스템은 두 복사본을 모두 유지해야 하며 이에 따라 실행 시간이 늦어집니다. 예를 들어 `_putenv`를 호출할 때마다 `_wputenv`에 대한 호출도 자동으로 실행되어 두 환경 문자열이 일치하게 됩니다.

> [!CAUTION]
> 드문 경우지만, 런타임 시스템이 유니코드 버전과 멀티바이트 버전의 환경을 모두 유지할 때 두 환경 버전이 정확히 일치하지 않을 수도 있습니다. 이는 고유한 멀티바이트 문자열이 고유한 유지코드 문자열에 매핑되지만 고유 유니코드 문자열에서 멀티바이트 문자열로 매핑이 반드시 고유하지는 않기 때문입니다. 따라서 두 개의 고유한 유니코드 문자열이 동일한 멀티바이트 문자열에 매핑될 수 있습니다.

[/MD](../build/reference/md-mt-ld-use-run-time-library.md) 또는 `/MDd` 링크가 사용될 때는 유니코드 컨텍스트에서 `_environ`을 폴링하는 것이 의미가 없습니다. CRT DLL에의 경우, 프로그램의 (와이드 또는 멀티바이트) 형식을 알 수 없습니다. 멀티바이트 형식이 가장 가능성이 높은 시나리오이기 때문에 이 형식만 생성됩니다.

다음 의사 코드에서는 이런 작업이 발생할 수 있는 방법을 보여 줍니다.

```
int i, j;
i = _wputenv( "env_var_x=string1" );  // results in the implicit call:
                                      // putenv ("env_var_z=string1")
j = _wputenv( "env_var_y=string2" );  // also results in implicit call:
                                      // putenv("env_var_z=string2")
```

이 예제에서 사용된 표기법에서 문자열은 C 문자열 리터럴이 아니라 `_wputenv` 호출에서는 유니코드 환경 문자열 리터럴을 나타내는 자리 표시자이고 `putenv` 호출에서는 멀티바이트 환경 문자열입니다. 두 개의 고유 유니코드 환경 문자열에서 문자 자리 표시자 '`x`' 및 '`y`'는 현재 MBCS의 문자에 고유하게 매핑되지 않습니다. 대신, 두 자리 표시자 모두 문자열 변환 시의 기본 결과인 일부 MBCS 문자 '`z`'에 매핑됩니다.

따라서 멀티바이트 환경에서 `putenv`에 대한 첫 번째 암시적 호출 이후에 "`env_var_z`"의 값은 "`string1`"이지만, 이 값은 `putenv`에 대한 두 번째 암시적 호출 발생 시 덮어써집니다("`env_var_z`"의 값이 "`string2`"로 설정된 경우). 따라서, 이 호출 계열 이후에 유니코드 환경(`_wenviron`에서)과 멀티바이트 환경(`_environ`에서)이 달라집니다.

## <a name="see-also"></a>참고 항목

[전역 변수](../c-runtime-library/global-variables.md)<br/>
[getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)<br/>
[getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)<br/>
[_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)<br/>
[_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)
