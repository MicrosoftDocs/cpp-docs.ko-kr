---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4951'
title: 컴파일러 경고(수준 1) C4951
ms.date: 08/27/2018
f1_keywords:
- C4951
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
ms.openlocfilehash: effb1f5af0c406de002b5c0b8522e7c58a2424a5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327967"
---
# <a name="compiler-warning-level-1-c4951"></a>컴파일러 경고(수준 1) C4951

> 프로필 데이터가 수집 된 이후 '*function*'이 편집 되었습니다. 함수 프로필 데이터가 사용 되지 않습니다.

[/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)에 대한 입력 모듈에서 함수가 편집되어 이제 프로필 데이터가 유효하지 않습니다. **/LTCG:PGINSTRUMENT** 후에 입력 모듈이 다시 컴파일되었으며,*/LTCG:PGINSTRUMENT* 작업 시 모듈에 있던 것과 다른 제어 흐름을 가진 함수( **function** )가 있습니다.

이 경고는 정보 제공용입니다. 이 경고를 해결하려면 **/LTCG:PGINSTRUMENT** 를 실행하고 모든 테스트 실행을 다시 실행한 다음 **/LTCG:PGOPTIMIZE** 를 실행합니다.

**/LTCG:PGOPTIMIZE** 를 사용한 경우 이 경고는 오류로 대체됩니다.
