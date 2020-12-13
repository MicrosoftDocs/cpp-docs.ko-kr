---
description: '자세한 정보: 심각한 오류 C1084'
title: 심각한 오류 C1084
ms.date: 11/04/2016
f1_keywords:
- C1084
helpviewer_keywords:
- C1084
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
ms.openlocfilehash: 6a3221bb894c0b320642a923d9552a207a2ff9ed
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145316"
---
# <a name="fatal-error-c1084"></a>심각한 오류 C1084

다음 파일 형식 파일을 읽을 수 없습니다. 'file': message

이 오류는 일반적으로 컴파일러에서 수행한 내부 시스템 API 호출 실패의 결과입니다. 이 오류가 발생할 때 표시 되는 메시지는 [_wcserror_s](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) 또는 [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage)에 의해 생성 되는 경우가 많습니다.

다음 단계를 수행하면 C1084 오류를 해결하는 데 도움이 될 수 있습니다.

- 지정한 파일이 있는지 확인합니다.

- 지정한 파일에 액세스하는 데 적절한 권한이 설정되어 있는지 확인합니다.

- 명령줄 구문이 [컴파일러 Command-Line 구문](../../build/reference/compiler-command-line-syntax.md)에 설명 된 규칙을 준수 하는지 확인 합니다.

- 이러한 환경 변수가 참조 하는 디렉터리에 액세스 하기 위해 환경 변수 **TMP** 및 **TEMP** 가 적절 하 게 설정 되었는지 확인 하 고 적절 한 사용 권한을 확인 합니다. 또한 **TMP** 및 **TEMP** 환경 변수에 의해 참조 되는 드라이브에 사용 가능한 공간이 충분 한지 확인 합니다.

- "잘못된 파일 번호"라는 메시지가 표시되면 백그라운드에서 컴파일하는 동안 지정한 파일이 전경에서 닫혀 있을 수 있습니다.

위의 진단을 수행한 후 클린 빌드를 수행합니다.
