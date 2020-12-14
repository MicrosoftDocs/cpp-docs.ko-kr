---
description: '자세한 정보: CL 옵션 순서'
title: CL 옵션 순서 (c + +)-Visual Studio
ms.date: 12/14/2018
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
ms.openlocfilehash: bc0290164ff40cf45d8d0a1e9f07e683e408c251
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226417"
---
# <a name="order-of-cl-options"></a>CL 옵션 순서

옵션은 마지막에 발생 해야 하는/link 옵션을 제외 하 고 CL 명령줄의 어디에 나 나타날 수 있습니다. 컴파일러는 [CL 환경 변수에](cl-environment-variables.md) 지정 된 옵션으로 시작한 다음, 명령 파일을 순서 대로 처리 하 여 왼쪽에서 오른쪽으로 명령 파일을 읽습니다. 각 옵션은 명령줄의 모든 파일에 적용 됩니다. CL은 충돌 하는 옵션을 발견할 경우 가장 오른쪽에 있는 옵션을 사용 합니다.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
