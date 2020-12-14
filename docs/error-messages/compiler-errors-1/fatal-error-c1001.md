---
description: '자세한 정보: 심각한 오류 C1001'
title: 심각한 오류 C1001
ms.date: 11/04/2016
f1_keywords:
- C1001
helpviewer_keywords:
- C1001
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
ms.openlocfilehash: a00e8bc2fe79201f77f67eac6f0756e90eba462b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262830"
---
# <a name="fatal-error-c1001"></a>심각한 오류 C1001

> 내부 컴파일러 오류 (컴파일러 파일 *파일*, 줄 *번호*)

컴파일러는 특정 식과 최적화 옵션의 조합 또는 구문 분석 문제 때문에 구문에 대 한 올바른 코드를 생성할 수 없습니다. 나열 된 컴파일러 파일에 utc 또는 C2 경로 세그먼트가 있는 경우 최적화 오류일 수 있습니다. 파일에 cxxfe 또는 c1xx 경로 세그먼트가 있거나이 msc1 인 경우 파서 오류일 수 있습니다. 이라는 파일이 cl.exe 경우 다른 정보를 사용할 수 없습니다.

하나 이상의 최적화 옵션을 제거 하 여 최적화 문제를 해결할 수 있는 경우가 많습니다. 오류에 해당 하는 옵션을 확인 하려면 한 번에 하나씩 옵션을 제거 하 고 오류 메시지가 사라질 때까지 다시 컴파일하십시오. 가장 일반적으로 발생 하는 옵션은 [/og (전역 최적화)](../../build/reference/og-global-optimizations.md) 및 [/Oi (내장 함수 생성)](../../build/reference/oi-generate-intrinsic-functions.md)입니다. 담당 하는 최적화 옵션을 결정 한 후에는 [optimize](../../preprocessor/optimize.md) pragma를 사용 하 여 오류가 발생 하는 함수를 사용 하지 않도록 설정 하 고 나머지 모듈에 옵션을 계속 사용할 수 있습니다. 최적화 옵션에 대 한 자세한 내용은 [최적화 모범 사례](../../build/optimization-best-practices.md)를 참조 하세요.

오류가 발생 하지 않을 경우에는 오류가 보고 되는 줄을 다시 작성 하거나 해당 줄을 둘러싼 몇 줄의 코드를 다시 작성 합니다. 전처리 후 컴파일러가이를 확인 하는 방식으로 코드를 보려면 [/p (파일로 전처리)](../../build/reference/p-preprocess-to-a-file.md) 옵션을 사용할 수 있습니다.

오류의 출처를 격리 하는 방법과 내부 컴파일러 오류를 Microsoft에 보고 하는 방법에 대 한 자세한 내용은 [Visual C++ 도구 집합을 사용 하 여 문제를 보고 하는 방법](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md)을 참조 하세요.
