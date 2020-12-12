---
description: 에 대해 자세히 알아보세요. BSCMAKE에서을 빌드하는 방법입니다. .Bsc 파일
title: BSCMAKE에서 .Bsc 파일을 빌드하는 방법
ms.date: 11/04/2016
helpviewer_keywords:
- browse information files (.bsc), building
ms.assetid: 8512b33e-c856-44a2-87bd-01ab10b52a95
ms.openlocfilehash: 6d468f365f7f42be2eb393e53d72053b682ec65a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191383"
---
# <a name="how-bscmake-builds-a-bsc-file"></a>BSCMAKE에서 .Bsc 파일을 빌드하는 방법

BSCMAKE는 가장 효율적으로 사용할 수 있는 방식으로 .bsc 파일을 빌드하거나 다시 빌드합니다. 잠재적인 문제를 방지 하려면 빌드 프로세스를 이해 하는 것이 중요 합니다.

BSCMAKE는 찾아보기 정보 파일을 빌드할 때 .sbr 파일을 0 길이로 자릅니다. 동일한 파일의 후속 빌드 중에는 길이가 0 인 (또는 비어 있는) .sbr 파일이 BSCMAKE에 게 새 기여를 갖지 않는다는 것을 알 수 있습니다. 이를 통해 BSCMAKE는 파일의 해당 부분에 대 한 업데이트가 필요 하지 않으며 증분 빌드도 충분 하다는 사실을 알 수 있습니다. /N 옵션이 지정 되지 않은 경우 모든 빌드 중에 BSCMAKE는 먼저 변경 된 .sbr 파일만 사용 하 여 파일을 증분 업데이트 하려고 시도 합니다.

BSCMAKE는/o 옵션을 사용 하 여 이름이 지정 된 .bsc 파일을 찾습니다. /O를 지정 하지 않으면 BSCMAKE는 첫 번째 .sbr 파일의 기본 이름 및 .bsc 확장명을 가진 파일을 찾습니다. 파일이 있으면 BSCMAKE는 영향을 주는 .sbr 파일만 사용 하 여 찾아보기 정보 파일의 증분 빌드를 수행 합니다. 파일이 없으면 BSCMAKE는 모든 .sbr 파일을 사용 하 여 전체 빌드를 수행 합니다. 빌드에 대 한 규칙은 다음과 같습니다.

- 전체 빌드를 성공적으로 수행 하려면 지정 된 모든 .sbr 파일이 있어야 하며 잘리지 않아야 합니다. .Sbr 파일이 잘린 경우 BSCMAKE를 실행 하기 전에 다시 컴파일하거나 취합 하 여 다시 빌드해야 합니다.

- 증분 빌드가 성공 하려면 .bsc 파일이 있어야 합니다. 모든 영향을 주는 .sbr 파일 (빈 파일)도 존재 해야 하며, BSCMAKE 명령줄에서 지정 해야 합니다. 명령줄에서 .sbr 파일을 생략 하면 BSCMAKE는 파일에서 해당 기여를 제거 합니다.

## <a name="see-also"></a>참고 항목

[빌드. .Bsc 파일](building-a-dot-bsc-file.md)
