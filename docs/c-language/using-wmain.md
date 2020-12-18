---
description: '자세한 정보: wmain 사용'
title: wmain 사용
ms.date: 11/04/2016
helpviewer_keywords:
- wmain function
ms.assetid: d0300812-adc4-40c6-bba3-b2da25468c80
ms.openlocfilehash: 575637700924876ffb3b54a4ea23dc2b62e5feb6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198936"
---
# <a name="using-wmain"></a>wmain 사용

**Microsoft 전용**

유니코드 프로그래밍 모델에서 **main** 함수의 와이드 문자 버전을 정의할 수 있습니다. 유니코드 프로그래밍 모델을 준수하는 이식 가능한 코드를 작성하려는 경우 **main** 대신 **wmain** 을 사용합니다.

## <a name="syntax"></a>구문

```
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )
```

## <a name="remarks"></a>설명

**main** 과 유사한 형식을 사용하여 **wmain** 에 대한 정식 매개 변수를 선언합니다. 와이드 문자 인수 또는 와이드 문자 환경 포인터를 프로그램에 전달할 수 있습니다. **wmain** 에 대한 `argv` 및 `envp` 매개 변수는 `wchar_t*` 형식입니다. 예를 들어:

프로그램이 **main** 함수를 사용하면 프로그램을 시작할 때 런타임 라이브러리에 의해 멀티바이트 문자 환경이 만들어집니다. 이 환경의 와이드 문자 복사본은 필요한 경우(예: `_wgetenv` 또는 `_wputenv` 함수를 호출하는 경우)에만 만들어집니다. `_wputenv` 또는 `_wgetenv`의 첫 번째 호출에서 MBCS 환경이 이미 있는 경우 해당 와이드 문자 문자열 환경이 만들어지고 `_wenviron` 전역 변수의 와이드 문자 버전인 `_environ` 전역 변수에 의해 가리킵니다. 이 시점에서 환경 복사본 두 개(MBCS와 유니코드)가 동시에 존재하며 프로그램의 수명 내내 운영 체제에 의해 유지 관리됩니다.

마찬가지로 프로그램이 **wmain** 함수를 사용하면 프로그램이 시작될 때 와이드 문자 환경이 만들어지고 `_wenviron` 전역 변수가 해당 환경을 가리킵니다. MBCS(ASCII) 환경은 `_putenv` 또는 `getenv`를 처음 호출할 때 만들어지며, `_environ` 전역 변수가 이 환경을 가리킵니다.

MBCS 환경에 대한 자세한 내용은 *런타임 라이브러리 참조* 에서 [국제화](../c-runtime-library/internationalization.md)를 참조하세요.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[main 함수 및 프로그램 실행](../c-language/main-function-and-program-execution.md)
