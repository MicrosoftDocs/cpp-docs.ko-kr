---
description: '자세한 정보: putch'
title: putch
ms.date: 12/16/2019
api_name:
- putch
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- putch
helpviewer_keywords:
- putch function
ms.assetid: 81e733e5-770e-4c7a-b7e4-8e66da109f92
ms.openlocfilehash: a7a5044e9ed59b1c6438ef3985307bdfe7bbb487
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97246333"
---
# <a name="putch"></a>putch

Microsoft 전용 함수 이름은 `putch` [_putch](putch-putwch.md) 함수에 사용 되지 않는 별칭입니다. 기본적으로 [컴파일러 경고 (수준 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)를 생성 합니다. 이름은 구현 관련 이름에 대해 표준 C 규칙을 따르지 않으므로 사용 되지 않습니다. 그러나 함수는 여전히 지원 됩니다.

대신 [_putch](putch-putwch.md) 를 사용 하는 것이 좋습니다. 또는이 함수 이름을 계속 사용 하 고 경고를 사용 하지 않도록 설정할 수 있습니다. 자세한 내용은 [경고](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) 및 [POSIX 함수 이름](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)해제를 참조 하세요.

> [!IMPORTANT]
> 이 API는 Windows 런타임에서 실행되는 애플리케이션에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.
