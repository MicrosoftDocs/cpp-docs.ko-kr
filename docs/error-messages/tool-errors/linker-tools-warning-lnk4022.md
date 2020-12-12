---
description: '자세한 정보: 링커 도구 경고 LNK4022'
title: 링커 도구 경고 LNK4022
ms.date: 11/04/2016
f1_keywords:
- LNK4022
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
ms.openlocfilehash: f0f968bf8e562d87e2227fb67f7a37b450c813b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331935"
---
# <a name="linker-tools-warning-lnk4022"></a>링커 도구 경고 LNK4022

' symbol ' 기호에 대해 고유한 일치 항목을 찾을 수 없습니다.

LINK 또는 LIB에서 지정 된 데코레이팅되지 않은 기호에 대해 여러 개의 일치 항목을 발견 하 여 모호성을 해결할 수 없습니다. 출력 파일 (.exe, .dll, .exp 또는 .lib)이 생성 되지 않습니다. 이 경고 다음에는 각 중복 기호에 대 한 하나의 경고 [LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) , 마지막으로 심각한 오류 [LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md)가 나옵니다.

이 경고를 방지 하려면 데코레이팅된 형식으로 기호를 지정 합니다. 개체에 대해 [DUMPBIN](../../build/reference/dumpbin-options.md) 을 실행 하 여 데코레이팅된 이름을 확인 합니다.
