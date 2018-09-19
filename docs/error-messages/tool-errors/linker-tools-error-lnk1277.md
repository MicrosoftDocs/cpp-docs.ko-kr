---
title: 링커 도구 오류 LNK1277 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1277
dev_langs:
- C++
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 542c48bd23b3f84ab301404987c77d964f51823e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082536"
---
# <a name="linker-tools-error-lnk1277"></a>링커 도구 오류 LNK1277

pgd (filename)에서 찾을 수 없는 개체 레코드

사용 하는 경우 [/LTCG:PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md)을 하나 입력된.lib, def, 또는.obj 파일의 경로 경로 /ltcg: pginstrument 중 발견 된는 다릅니다. 이 /ltcg: pginstrument 후 LIB 환경 변수 변경으로 설명 될 수 있습니다. 입력 파일의 전체 경로.pgd 파일에 저장 됩니다.

/Ltcg: pgoptimize에서는 입력 /ltcg: pginstrument 단계와 동일 합니다.

이 경고를 해결 하려면 다음 중 하나를 수행 합니다.

- /Ltcg: pginstrument 실행, 모든 테스트 실행을 다시 실행 하 고 /ltcg: pgoptimize를 실행 합니다.

- /Ltcg: pginstrument 실행 한 때에 LIB 환경 변수를 변경 합니다.

/Ltcg: pgupdate를 사용 하 여 LNK1277을 해결 하는 권장 되지 않습니다.