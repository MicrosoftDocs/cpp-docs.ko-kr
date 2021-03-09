---
title: CRT의 보안 기능
description: Microsoft C 런타임의 보안 CRT 함수에 대 한 개요입니다.
ms.date: 09/29/2020
ms.topic: conceptual
f1_keywords:
- _CRT_SECURE_NO_DEPRECATE
- _CRT_NONSTDC_NO_WARNINGS
- _CRT_SECURE_NO_WARNINGS
helpviewer_keywords:
- security deprecation warnings [C++]
- CRT_NONSTDC_NO_DEPRECATE
- buffers [C++], buffer overruns
- deprecation warnings (security-related), disabling
- _CRT_NONSTDC_NO_WARNINGS
- security [CRT]
- _CRT_SECURE_NO_WARNINGS
- _CRT_NONSTDC_NO_DEPRECATE
- _CRT_SECURE_NO_DEPRECATE
- security-enhanced CRT
- CRT_SECURE_NO_WARNINGS
- CRT_SECURE_NO_DEPRECATE
- deprecation warnings (security-related)
- buffer overruns
- CRT_NONSTDC_NO_WARNINGS
- CRT, security enhancements
- parameters [C++], validation
ms.assetid: d9568b08-9514-49cd-b3dc-2454ded195a3
ms.openlocfilehash: 96642e5e79f9df7c0a063582408c0463600be20f
ms.sourcegitcommit: 90c300b74f6556cb5d989802d2e80d79542f55e7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102514683"
---
# <a name="security-features-in-the-crt"></a>CRT의 보안 기능

이전 CRT 함수 중 상당수에 더 안전한 최신 버전이 있습니다. 안전한 함수가 있을 경우 보안 수준이 떨어지는 이전 버전이 사용되지 않는 것으로 표시되고 새 버전에 `_s`("안전함") 접미사가 붙습니다.

이 컨텍스트에서 "사용 되지 않음"은 함수를 사용 하지 않는 것을 의미 합니다. 함수가 CRT에서 제거 되도록 예약 되어 있음을 의미 하지 않습니다.

보안 함수는 보안 오류를 방지 하거나 수정 하지 않습니다. 대신 오류가 발생 하는 경우 오류를 catch 합니다. 오류 조건에 대 한 추가 검사를 수행 합니다. 오류가 있는 경우 오류 처리기를 호출 합니다 ( [매개 변수 유효성 검사](../c-runtime-library/parameter-validation.md)참조).

예를 들어 `strcpy` 함수는 복사 하는 문자열이 대상 버퍼에 비해 너무 큰지 확인할 수 없습니다. 이에 상응 하는 보안은 `strcpy_s` 버퍼의 크기를 매개 변수로 사용 합니다. 따라서 버퍼 오버런이 발생 하는지 확인할 수 있습니다. 을 사용 하 여 `strcpy_s` 11 자를 10 자 버퍼로 복사할 경우이는 사용자의 오류입니다. 사용자의 `strcpy_s` 실수를 수정할 수 없습니다. 그러나 잘못 된 매개 변수 처리기를 호출 하 여 오류를 감지 하 고 사용자에 게 알릴 수 있습니다.

## <a name="eliminating-deprecation-warnings"></a>사용되지 않음 경고 제거

보안 수준이 떨어지는 이전 함수에 대한 사용되지 않음 경고는 여러 가지 방법으로 제거할 수 있습니다. 가장 간단한 방법은 단순히 `_CRT_SECURE_NO_WARNINGS`를 정의하거나 [warning](../preprocessor/warning.md) pragma를 사용하는 것입니다. 사용 중단 경고가 사용 되지 않도록 설정 되지만 경고를 발생 시킨 보안 문제는 여전히 존재 합니다. 사용 중단 경고를 사용 하도록 설정 하 고 새로운 CRT 보안 기능을 활용 하는 것이 좋습니다.

C + +에서이 작업을 수행 하는 가장 쉬운 방법은 [안전한 템플릿 오버 로드](../c-runtime-library/secure-template-overloads.md)를 사용 하는 것입니다. 이렇게 하면 더 이상 사용 되지 않는 함수에 대 한 호출을 해당 함수의 안전한 버전에 대 한 호출로 바꿔서 사용 중단 경고가 제거 됩니다. 예를 들어 `strcpy`에 대한 사용되지 않는 다음 호출을 살펴보십시오.

```
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

`_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES`를 1로 정의하면 `strcpy` 호출이 버퍼 오버런을 방지하는 `strcpy_s`로 변경되어 경고가 제거됩니다. 자세한 내용은 [안전한 템플릿 오버로드](../c-runtime-library/secure-template-overloads.md)를 참조하세요.

사용되지 않는 함수 중 안전한 템플릿 오버로드가 없는 함수의 경우 안전한 버전을 사용하도록 수동으로 코드를 업데이트해야 합니다.

보안과 관련되지는 않았지만 사용되지 않음 경고의 원인이 되는 또 다른 항목은 POSIX 함수입니다. POSIX 함수 이름을 표준 상응 항목으로 대체하거나(예: [access](../c-runtime-library/reference/access-crt.md)를 [_access](../c-runtime-library/reference/access-waccess.md)로 변경) `_CRT_NONSTDC_NO_WARNINGS`를 정의하여 POSIX 관련 사용되지 않음 경고가 표시되지 않게 만듭니다. 자세한 내용은 [호환성](compatibility.md)을 참조하세요.

## <a name="additional-security-features"></a>추가 보안 기능

보안 기능에는 다음이 포함 됩니다.

- `Parameter Validation`. 안전한 함수 및 안전 하지 않은 해당 하는 대부분의 매개 변수 유효성 검사 유효성 검사는 다음을 포함할 수 있습니다.

  - **NULL** 값을 확인 하는 중입니다.
  - 열거형 값의 유효성
  - 정수 계열 값이 유효 범위 내에 있는지 여부

- 자세한 내용은 [매개 변수 유효성 검사](../c-runtime-library/parameter-validation.md)를 참조하세요.

- 개발자가 잘못된 매개 변수에 대한 처리기에도 액세스할 수 있습니다. 함수에서 응용 프로그램을 어설션 및 종료 하는 대신 잘못 된 매개 변수가 발견 되 면 CRT를 사용 하 여 [_set_invalid_parameter_handler _set_thread_local_invalid_parameter_handler를](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)통해 이러한 문제를 확인할 수 있습니다.

- `Sized Buffers`. 버퍼에 쓰는 모든 보안 함수에 버퍼 크기를 전달 해야 합니다. 안전한 버전은 버퍼에 쓰기 전에 버퍼가 충분히 큰지 확인 합니다. 악의적인 코드를 실행할 수 있는 위험한 버퍼 오버런 오류를 방지 하는 데 도움이 됩니다. 이러한 함수는 일반적으로 `errno` 오류 코드를 반환 하 고 버퍼 크기가 너무 작을 경우 잘못 된 매개 변수 처리기를 호출 합니다. `gets`와 같이 입력 버퍼에서 읽는 함수에는 최대 크기를 지정해야 하는 안전한 버전이 있습니다.

- `Null termination`. 종료 되지 않은 문자열을 남겨진 일부 함수에는 문자열이 적절 하 게 null로 종료 되도록 하는 안전한 버전이 있습니다.

- `Enhanced error reporting`. Secure 함수는 기존 함수에서 사용할 수 있었던 것 보다 더 많은 오류 정보와 함께 오류 코드를 반환 합니다. 보안 함수 및 기존 함수 대부분은 `errno` `errno` 더 나은 오류 보고를 제공 하기 위해 코드 형식을 반환 하 고 자주 반환 됩니다.

- `Filesystem security`. 안전한 파일 I/O API는 default case에서 안전한 파일 액세스를 지원합니다.

- `Windows security`. 안전한 프로세스 API는 보안 정책을 적용하고 ACL을 지정할 수 있게 허용합니다.

- `Format string syntax checking`. 잘못된 문자열이 검색됩니다(예:`printf` 형식 문자열에 잘못된 형식 필드 문자 사용).

## <a name="see-also"></a>추가 정보

[매개 변수 유효성 검사](../c-runtime-library/parameter-validation.md)<br/>
[안전한 템플릿 오버 로드](../c-runtime-library/secure-template-overloads.md)<br/>
[CRT (c 런타임) 및 STL (c + + 표준 라이브러리) `.lib` 파일](../c-runtime-library/crt-library-features.md)
