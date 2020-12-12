---
description: '자세한 정보: CRT에 연결 하는 데 사용 되는 메서드의 이점 및 장단점'
title: CRT에 연결 하는 데 사용 되는 메서드의 장단점
ms.date: 05/06/2019
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 49b485f7-9487-49e4-b12a-0f710b620e2b
ms.openlocfilehash: 763332de9615e978d84902f67f2c97efd0767c89
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148527"
---
# <a name="benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt"></a>CRT에 연결 하는 데 사용 되는 메서드의 장단점

프로젝트는 동적 또는 정적으로 CRT와 연결할 수 있습니다. 아래 표에서는 사용할 방법을 선택 하는 것과 관련 된 장단점을 간략하게 설명 합니다.

|메서드|이점|균형|
|------------|-------------|--------------|
|CRT에 정적으로 연결<br /><br /> (**런타임 라이브러리** 를 **단일 스레드로** 설정)|이미지가 실행 될 시스템에는 CRT DLL이 필요 하지 않습니다.|25,000의 시작 코드에 대 한 정보는 이미지에 추가 되어 크기가 크게 증가 합니다.|
|CRT에 동적으로 연결<br /><br /> (**런타임 라이브러리** 를 **다중 스레드로** 설정)|이미지에는 CRT 시작 코드가 필요 하지 않으므로 훨씬 더 작습니다.|CRT DLL은 이미지를 실행 하는 시스템에 있어야 합니다.|

[ATL 프로젝트에서 crt에 연결](../atl/linking-to-the-crt-in-your-atl-project.md) 항목은 crt에 연결할 방식을 선택 하는 방법을 설명 합니다.

## <a name="see-also"></a>참고 항목

[ATL 및 C Run-Time 코드를 사용한 프로그래밍](../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[DLL 및 Visual C++ 런타임 라이브러리 동작](../build/run-time-library-behavior.md)<br/>
[CRT 라이브러리 기능](../c-runtime-library/crt-library-features.md)
