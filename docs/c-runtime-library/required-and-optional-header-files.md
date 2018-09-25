---
title: 필수 및 선택적 헤더 파일 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.headers
dev_langs:
- C++
helpviewer_keywords:
- include files, required in run time
- header files, required in run time
ms.assetid: f64d0bf5-e2c3-4b42-97d0-443b3d901d9f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: afd523bad5d70cdfc80a6e8a532b2409be535c6b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091870"
---
# <a name="required-and-optional-header-files"></a>필수 및 선택적 헤더 파일

각 런타임 루틴에 대한 설명에는 해당 루틴의 필수 및 선택적 포함 또는 헤더(.H) 파일의 목록이 포함됩니다. 루틴에 대한 함수 선언 또는 내부적으로 호출되는 다른 루틴에 사용되는 정의를 가져오려면 필수 헤더 파일을 포함해야 합니다. 선택적 헤더 파일은 미리 정의된 상수, 형식 정의 또는 인라인 매크로를 활용하기 위해 일반적으로 포함됩니다. 다음 표에서는 선택적 헤더 파일 콘텐츠의 몇 가지 예를 나열합니다.

|정의|예|
|----------------|-------------|
|매크로 정의|라이브러리 루틴이 매크로로 구현되는 경우 원래 루틴에 대한 헤더 파일이 아닌 다른 헤더 파일에 매크로 정의가 있을 수 있습니다. 예를 들어 `_toupper` 매크로는 헤더 파일 CTYPE.H에 정의되고 `toupper` 함수는 STDLIB.H에 선언됩니다.|
|미리 정의된 상수|많은 라이브러리 루틴이 헤더 파일에 정의된 상수를 참조합니다. 예를 들어 `_open` 루틴은 헤더 파일 FCNTL.H에 정의된 `_O_CREAT`와 같은 상수를 사용합니다.|
|형식 정의|일부 라이브러리 루틴은 구조를 반환하거나 구조를 인수로 사용합니다. 예를 들어 스트림 입/출력 루틴은 STDIO.H에 정의된 `FILE` 형식의 구조를 사용합니다.|

런타임 라이브러리 헤더 파일은 ANSI/ISO C 표준 권장 스타일로 함수 선언을 제공합니다. 컴파일러는 연결된 함수 선언 후에 발생하는 모든 루틴 참조에 대해 형식 검사를 수행합니다. 함수 선언은 기본값인 `int`가 아닌 일부 형식의 값을 반환하는 루틴의 경우 특히 중요합니다. 컴파일러는 해당 선언에 적절한 반환 값을 지정하지 않는 루틴이 예기치 않은 결과를 발생시킬 수 있는 `int`를 반환하는 것으로 간주합니다. 자세한 내용은 [형식 검사](../c-runtime-library/type-checking-crt.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

[CRT 라이브러리 기능](../c-runtime-library/crt-library-features.md)