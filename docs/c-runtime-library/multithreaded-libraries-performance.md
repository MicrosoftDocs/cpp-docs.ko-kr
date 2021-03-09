---
title: 다중 스레드 라이브러리 성능
description: Microsoft C 런타임 다중 스레드 라이브러리에서 성능을 최대한 활용 하는 방법에 대 한 개요입니다.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- threading [C++], performance
- libraries, multithreaded
- performance, multithreading
- multithreaded libraries
ms.assetid: faa5d808-087c-463d-8f0d-8c478d137296
ms.openlocfilehash: 39d77d52dbc8ac2e725cf46c98c5462df701e3eb
ms.sourcegitcommit: 90c300b74f6556cb5d989802d2e80d79542f55e7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102514670"
---
# <a name="multithreaded-libraries-performance"></a>다중 스레드 라이브러리 성능

단일 스레드 CRT는 더 이상 사용할 수 없습니다. 이 항목에서는 다중 스레드 라이브러리에서 최대 성능을 얻는 방법에 대해 설명합니다.

## <a name="maximizing-performance"></a>성능 극대화

다중 스레드 라이브러리의 성능이 개선되어 지금은 제거된 단일 스레드 라이브러리의 성능에 근접하게 되었습니다. 더 높은 성능이 필요한 경우를 위해 여러 가지 새로운 기능이 추가되었습니다.

- 독립적인 스트림 잠금 기능을 통해 스트림을 잠근 다음 스트림에 직접 액세스하는 [_nolock 함수](../c-runtime-library/nolock-functions.md)를 사용할 수 있습니다. 이로 인해 중요한 루프 외부에서 잠금 사용을 해제할 수 있습니다.

- 스레드별 로캘은 다중 스레드 시나리오에 대해 로캘 액세스 비용을 줄여 줍니다([_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) 참조).

- 로캘 종속 함수(이름이 _l로 끝남)는 로캘을 매개 변수로 사용하여 비용을 상당히 절감합니다(예: [printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)).

- 공통 코드 페이지에 대한 최적화는 많은 짧은 작업의 비용을 절감합니다.

- [_CRT_DISABLE_PERFCRIT_LOCKS](../c-runtime-library/crt-disable-perfcrit-locks.md)를 정의하면 모든 I/O 작업이 단일 스레드 I/O 모델을 가정하고 함수의 _nolock 형태를 사용하게 됩니다. 이로 인해 상당히 I/O를 기반으로 하는 단일 스레드 애플리케이션의 성능이 향상됩니다.

- CRT 힙 핸들을 노출하면 CRT 힙에 대해 Windows LFH(낮은 조각화 힙)가 가능해져 규모가 큰 시나리오에서 성능이 상당히 개선될 수 있습니다.

## <a name="see-also"></a>추가 정보

[CRT (c 런타임) 및 STL (c + + 표준 라이브러리) `.lib` 파일](../c-runtime-library/crt-library-features.md)
