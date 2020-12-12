---
description: '자세한 정보: 링커 도구 오류 LNK1245'
title: 링커 도구 오류 LNK1245
ms.date: 11/04/2016
f1_keywords:
- LNK1245
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
ms.openlocfilehash: 3903651992f8fb79c3a79e4f2afc9d84e70e8126
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193905"
---
# <a name="linker-tools-error-lnk1245"></a>링커 도구 오류 LNK1245

' subsystem ' 하위 시스템을 잘못 지정 했습니다. /SUBSYSTEM는 WINDOWS, WINDOWSCE 또는 CONSOLE 이어야 합니다.

[/clr](../../build/reference/clr-common-language-runtime-compilation.md) 을 사용 하 여 개체를 컴파일하고 다음 조건 중 하나에 해당 하는 경우

- 사용자 지정 진입점이 정의 되었습니다.[즉,](../../build/reference/entry-entry-point-symbol.md)링커가 하위 시스템을 유추할 수 없습니다.

- /Clr 개체에 대해 유효 하지 않은 [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) 링커 옵션에 값이 전달 되었습니다.

두 경우 모두 해결 방법은/SUBSYSTEM 링커 옵션에 대 한 유효한 값을 지정 하는 것입니다.
