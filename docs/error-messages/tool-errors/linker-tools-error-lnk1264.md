---
description: '자세한 정보: 링커 도구 오류 LNK1264'
title: 링커 도구 오류 LNK1264
ms.date: 11/04/2016
f1_keywords:
- LNK1264
helpviewer_keywords:
- LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
ms.openlocfilehash: 122186482800597780405ae89e8e01c008794756
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193788"
---
# <a name="linker-tools-error-lnk1264"></a>링커 도구 오류 LNK1264

/LTCG: PGINSTRUMENT 경우 지정 되었지만 코드를 생성할 필요가 없습니다. 계측 실패

**/Ltcg: PGINSTRUMENT** 지정 되었지만 [/gl](../../build/reference/gl-whole-program-optimization.md)을 사용 하 여 컴파일된 .obj 파일을 찾을 수 없습니다. 계측을 수행할 수 없고 링크에 오류가 발생 했습니다. 계측을 수행할 수 있도록 **/gl** 을 사용 하 여 컴파일된 명령줄에 .obj 파일이 하나 이상 있어야 합니다.

PGO (프로필 기반 최적화)는 64 비트 컴파일러 에서만 사용할 수 있습니다.
