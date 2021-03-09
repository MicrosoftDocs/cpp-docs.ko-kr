---
title: 매개 변수 유효성 검사
description: Microsoft C 런타임 라이브러리의 매개 변수 유효성 검사에 대 한 설명입니다.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parameters, validation
ms.assetid: 019dd5f0-dc61-4d2e-b4e9-b66409ddf1f2
ms.openlocfilehash: 6926da8ccc1974352b926227daba0eea1d8a560d
ms.sourcegitcommit: 90c300b74f6556cb5d989802d2e80d79542f55e7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102514657"
---
# <a name="parameter-validation"></a>매개 변수 유효성 검사

보안이 강화 된 CRT 함수 중 대부분은 **NULL** 에 대 한 포인터 검사, 정수가 올바른 범위에 포함 되는 경우 또는 열거형 값이 유효한 것과 같은 항목에 대해 매개 변수의 유효성을 검사 하지 않습니다. 잘못 된 매개 변수가 발견 되 면 잘못 된 매개 변수 처리기가 호출 됩니다.

## <a name="invalid-parameter-handler-routine"></a>잘못된 매개 변수 처리기 루틴

C 런타임 라이브러리 함수는 잘못 된 매개 변수를 검색 하는 경우 오류에 대 한 일부 정보를 캡처한 다음 잘못 된 매개 변수 처리기 디스패치 함수를 래핑하는 매크로를 호출 합니다. [_Invalid_parameter](../c-runtime-library/reference/invalid-parameter-functions.md), [_invalid_parameter_noinfo](../c-runtime-library/reference/invalid-parameter-functions.md)또는 [_invalid_parameter_noinfo_noreturn](../c-runtime-library/reference/invalid-parameter-functions.md)중 하나가 됩니다. 호출 되는 디스패치 함수는 코드가, 각각 디버그 빌드, 소매점 빌드 또는 오류를 복구할 수 없는 것으로 간주 되는지에 따라 달라 집니다.

디버그 빌드에서는 잘못 된 매개 변수 매크로가 디스패치 함수를 호출 하기 전에 일반적으로 실패 한 어설션 및 디버거 중단점을 발생 시킵니다. 코드를 실행 하면 운영 체제 및 런타임 라이브러리 버전에 따라 "중단", "다시 시도", "계속" 또는 유사한 선택 항목이 포함 된 대화 상자에서 어설션이 사용자에 게 보고 될 수 있습니다. 사용자는 이러한 옵션을 사용 하 여 프로그램을 즉시 종료 하거나, 디버거를 연결 하거나, 기존 코드를 계속 실행 하 여 디스패치 함수를 호출할 수 있습니다.

잘못 된 매개 변수 처리기 디스패치 함수는 현재 할당 된 잘못 된 매개 변수 처리기를 호출 합니다. 기본적으로 잘못 된 매개 변수는를 호출 하 여 `_invoke_watson` 응용 프로그램을 닫고 미니 덤프를 생성 합니다. 운영 체제에서 사용 하도록 설정 된 경우 분석을 위해 Microsoft로 크래시 덤프를 보낼지 여부를 묻는 대화 상자가 사용자에 게 표시 됩니다.

함수 [_set_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 또는 [_set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 를 사용 하 여 잘못 된 매개 변수 처리기를 고유한 함수로 설정 하면이 동작을 변경할 수 있습니다. 직접 지정하는 함수가 애플리케이션을 종료하지 않는 경우에는 잘못된 매개 변수를 수신한 함수에 컨트롤이 반환됩니다. CRT에서 이러한 함수는 일반적으로 함수 실행을 중지 하 `errno` 고, 오류 코드로 설정 하 고, 오류 코드를 반환 합니다. 대부분의 경우 `errno` 값과 반환 값은 모두 `EINVAL` 잘못 된 매개 변수를 나타내는입니다. 경우에 따라 매개 변수로 전달된, 잘못된 파일 포인터에 대한 `EBADF`와 같은 보다 구체적인 오류 코드가 반환됩니다.

`errno`에 대한 자세한 내용은 [errno, _doserrno, _sys_errlist 및 _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.

## <a name="see-also"></a>추가 정보

[CRT의 보안 기능](../c-runtime-library/security-features-in-the-crt.md)\
[CRT (c 런타임) 및 STL (c + + 표준 라이브러리) `.lib` 파일](../c-runtime-library/crt-library-features.md)
