---
description: '자세한 정보: 심각한 오류 C 1047'
title: 심각한 오류 C1047
ms.date: 02/17/2021
f1_keywords:
- C1047
helpviewer_keywords:
- C1047
ms.openlocfilehash: f22d7c7591e2c2c477d09f1637641cc351eeafb5
ms.sourcegitcommit: 5efc34c2b98d4d0d3e41aec38b213f062c19d078
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/04/2021
ms.locfileid: "101844483"
---
# <a name="fatal-error-c1047"></a>심각한 오류 C1047

> 개체 또는 라이브러리 파일 '*filename*'이 (가) 다른 개체 보다 이전 컴파일러로 만들어졌습니다. 이전 개체 및 라이브러리 다시 빌드

새 버전의 컴파일러를 사용 하 여 프로젝트를 빌드할 때 기존 개체 파일 또는 라이브러리를 완전히 다시 빌드하지 않는 경우이 오류가 발생할 수 있습니다.

## <a name="remarks"></a>설명

C 1047는 또는를 사용 하 여 빌드한 개체 파일 또는 **`/GL`** 라이브러리가 **`/LTCG`** 다른 버전의 Visual Studio C/c + + 컴파일러 도구 집합에서 함께 연결 될 때 발생 합니다. 예를 들어 visual **`/LTCG`** studio 2019 버전 16.7을 사용 하 여 빌드한 라이브러리를 Visual studio 2019 버전 16.8을 사용 하 여 빌드한 앱에 연결할 수 없습니다. 개체와 라이브러리를 컴파일하는 데 사용 되는 도구 집합의 주 및 부 업데이트 번호는 정확히 일치 해야 합니다.

C 1047를 해결 하려면 동일한 버전의 도구 집합을 사용 하 여 모든 개체 파일 또는 라이브러리를 다시 빌드하십시오.

## <a name="see-also"></a>참고 항목

[`/GL` (전체 프로그램 최적화)](../../build/reference/gl-whole-program-optimization.md)\
[`/LTCG` (링크 타임 코드 생성)](../../build/reference/ltcg-link-time-code-generation.md)\
[C++ 이진 호환성 2015-2019](../../porting/binary-compat-2015-2017.md)
