---
title: 코드 페이지
description: Microsoft C 런타임의 코드 페이지 지원에 대 한 설명입니다.
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- character sets [C++], code pages
- ANSI [C++], code pages
- system-default code page
- multibyte code pages [C++]
- localization [C++], code pages
- code pages [C++], types of
- locale code pages [C++]
ms.assetid: 4a26fc42-185a-4add-98bf-a7b314ae6186
ms.openlocfilehash: 1f9d311ec714d2043e072cbbfbac505d3f804294
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590071"
---
# <a name="code-pages"></a>코드 페이지

*코드 페이지*는 숫자, 문장 부호 및 기타 문자를 포함할 수 있는 문자 집합입니다. 언어 및 로캘마다 다른 코드 페이지를 사용할 수 있습니다. 예를 들어 ANSI 코드 페이지 1252는 미국 영어와 대부분의 유럽 언어에 사용되고, OEM 코드 페이지 932는 일본어 간지에 사용됩니다.

코드 페이지는 문자를 싱글바이트 또는 멀티 바이트 값으로 매핑하는 테이블로 나타낼 수 있습니다. 여러 코드 페이지는 0x00 - 0x7F 범위의 문자에 대한 ASCII 문자 집합을 공유합니다.

Microsoft 런타임 라이브러리는 다음 형식의 코드 페이지를 사용 합니다.

- 시스템 기본 ANSI 코드 페이지. 기본적으로 시작할 때 런타임 시스템은 자동으로 멀티 바이트 코드 페이지를 운영 체제에서 가져온 시스템 기본 ANSI 코드 페이지로 설정 합니다. 다음을 호출해도

    ```C
    setlocale ( LC_ALL, "" );
    ```

   로캘이 시스템 기본 ANSI 코드 페이지로 설정됩니다.

- 로캘 코드 페이지. 다양한 런타임 루틴의 동작은 로캘 코드 페이지를 포함하는 현재 로캘 설정에 따라 달라집니다. 자세한 내용은 [로캘 종속 루틴](../c-runtime-library/locale.md)을 참조 하세요. 기본적으로 Microsoft 런타임 라이브러리의 모든 로캘 종속 루틴은 "C" 로캘에 해당 하는 코드 페이지를 사용 합니다. 런타임에 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)을 호출 하 여 사용 중인 로캘 코드 페이지를 변경 하거나 쿼리할 수 있습니다.

- 멀티바이트 코드 페이지. 런타임 라이브러리에서 대부분의 멀티바이트 문자 루틴 동작은 현재 멀티바이트 코드 페이지 설정에 따라 달라집니다. 기본적으로 이러한 루틴은 시스템 기본 ANSI 코드 페이지를 사용합니다. 런타임 시 [_getmbcp](../c-runtime-library/reference/getmbcp.md) 및 [_setmbcp](../c-runtime-library/reference/setmbcp.md)를 각각 사용하여 멀티바이트 코드 페이지를 변경하거나 쿼리할 수 있습니다.

- "C" 로캘은 C 프로그램에서 일반적으로 실행하던 로캘에 해당되도록 ANSI에 의해 정의됩니다. "C" 로캘 코드 페이지("C" 코드 페이지)는 ASCII 문자 집합에 해당합니다. 예를 들어 "C" 로캘에서 **islower**는 0x61 - 0x7A의 값에 대해서만 true를 반환합니다. 다른 로캘에서 **islower** `true` 는 해당 로캘에 의해 정의 된 대로 이러한 값과 다른 값을 반환할 수 있습니다.

## <a name="see-also"></a>참고 항목

[국제화](../c-runtime-library/internationalization.md)\
[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)
