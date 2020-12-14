---
description: '자세한 정보: 메이크파일의 전처리의 식'
title: 메이크파일 전처리 식
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessing makefiles
- expressions [C++], makefile preprocessing
- makefiles, preprocessing
ms.assetid: 37f0f413-97e0-452c-a83f-3c9002c44c92
ms.openlocfilehash: 9b30900db493a2a87e0527e6f3c062185bb4ab43
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200795"
---
# <a name="expressions-in-makefile-preprocessing"></a>메이크파일 전처리 식

**! 이면이 고, 그렇지 않으면** **입니다. IF** `constantexpression` 는 정수 상수 (10 진수 또는 C 언어 표기법), 문자열 상수 또는 명령으로 구성 됩니다. 식을 그룹화 하려면 괄호를 사용 합니다. 식에서는 C 스타일의 부호 있는 정수 (long) 산술 연산을 사용 합니다. 숫자는-2147483648 ~ 2147483647 범위의 32 비트 2의 보수 형식으로 되어 있습니다.

식은 상수 값에 대해 작동 하는 연산자, 명령, 문자열, 매크로 및 파일 시스템 경로를 사용 하 여 코드를 종료할 수 있습니다.

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

[메이크파일 전처리 연산자](makefile-preprocessing-operators.md)

[전처리에서 프로그램 실행](executing-a-program-in-preprocessing.md)

## <a name="see-also"></a>참고 항목

[메이크파일 전처리](makefile-preprocessing.md)
