---
description: '자세한 정보: 링커 도구 오류 LNK1277'
title: 링커 도구 오류 LNK1277
ms.date: 11/04/2016
f1_keywords:
- LNK1277
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
ms.openlocfilehash: 82a71878d30088bd018c4e54216d53228efe949d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193736"
---
# <a name="linker-tools-error-lnk1277"></a>링커 도구 오류 LNK1277

pgd (파일 이름)에서 개체 레코드를 찾을 수 없습니다.

[/Ltcg: PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md)를 사용 하는 경우 입력 .lib, def 또는 .obj 파일 중 하나의 경로가/LTCG: pginstrument 때 발견 된 경로와 다릅니다. 이는/LTCG: PGINSTRUMENT 후 LIB 환경 변수를 변경 하 여 설명할 수 있습니다. 입력 파일에 대 한 전체 경로는 .pgd 파일에 저장 됩니다.

/LTCG: PGOPTIMIZE를 사용 하려면 입력이/LTCG: PGINSTRUMENT 단계와 동일 해야 합니다.

이 경고를 해결 하려면 다음 중 하나를 수행 합니다.

- /LTCG: PGINSTRUMENT를 실행 하 고 모든 테스트 실행을 다시 실행 한 다음/LTCG: PGOPTIMIZE를 실행 합니다.

- LIB 환경 변수를/LTCG: PGINSTRUMENT 때의 정의로 변경 합니다.

/LTCG: PGUPDATE를 사용 하 여 LNK1277를 해결 하는 것은 권장 되지 않습니다.
