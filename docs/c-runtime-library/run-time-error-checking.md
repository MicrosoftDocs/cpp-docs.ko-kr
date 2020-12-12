---
description: '자세한 정보: Run-Time 오류 검사'
title: 런타임 오류 검사
ms.date: 11/04/2016
helpviewer_keywords:
- run-time error checking
- run-time errors, checking
ms.assetid: c965dd01-57ad-4a3c-b1d6-5aa04f920501
ms.openlocfilehash: aff00bc66cd118b891e902328eb6ae85bd6fc14c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273607"
---
# <a name="run-time-error-checking"></a>런타임 오류 검사

C 런타임 라이브러리에는 RTC(런타임 오류 검사)를 지원하는 함수가 포함되어 있습니다. 런타임 오류 검사를 사용하면 특정 런타임 오류 종류가 보고되도록 프로그램을 빌드할 수 있습니다. 오류가 보고되는 방법과 보고되는 오류 종류를 지정합니다. 자세한 내용은 [방법: 네이티브 런타임 검사 기능 사용](/visualstudio/debugger/how-to-use-native-run-time-checks)을 참조하세요.

프로그램에서 런타임 오류 검사가 수행되는 방법을 사용자 지정하려면 다음 함수를 사용하십시오.

## <a name="run-time-error-checking-functions"></a>런타임 오류 검사 함수

|함수|기능|
|--------------|---------|
|[_RTC_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md)|런타임 오류 검사 형식에 대한 간단한 설명을 반환합니다.|
|[_RTC_NumErrors](../c-runtime-library/reference/rtc-numerrors.md)|런타임 오류 검사에서 발견될 수 있는 총 오류 수를 반환합니다.|
|[_RTC_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md)|런타임 오류 검사 보고를 위한 처리기로 함수를 지정합니다.|
|[_RTC_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md)|런타임 오류 검사에서 발견된 오류를 형식에 연결합니다.|

## <a name="see-also"></a>참고 항목

[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)<br/>
[/RTC (런타임 오류 검사)](../build/reference/rtc-run-time-error-checks.md)<br/>
[runtime_checks](../preprocessor/runtime-checks.md)<br/>
[디버그 루틴](../c-runtime-library/debug-routines.md)<br/>
