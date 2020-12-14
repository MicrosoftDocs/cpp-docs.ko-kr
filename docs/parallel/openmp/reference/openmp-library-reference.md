---
description: '자세히 알아보기: OpenMP 라이브러리 참조'
title: OpenMP 라이브러리 참조
ms.date: 12/02/2019
ms.assetid: a25188c6-edde-43d0-84b5-780e797b08fc
ms.openlocfilehash: fa1f654835afef94b0e00f52bebb0b7300d205be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342363"
---
# <a name="openmp-library-reference"></a>OpenMP 라이브러리 참조

OpenMP API에서 사용 되는 생성자에 대 한 링크를 제공 합니다.

OpenMP 표준의 Visual C++ 구현에는 다음 구문이 포함 됩니다.

|구문|설명|
|---------------|-----------------|
|[지시문](openmp-directives.md)|OpenMP API에서 사용 되는 지시문에 대 한 링크를 제공 합니다.|
|[절](openmp-clauses.md)|OpenMP API에서 사용 되는 절에 대 한 링크를 제공 합니다.|
|[함수](openmp-functions.md)|OpenMP API에서 사용 되는 함수에 대 한 링크를 제공 합니다.|
|[환경 변수](openmp-environment-variables.md)|OpenMP API에서 사용 되는 환경 변수에 대 한 링크를 제공 합니다.|

Visual C++ OpenMP 런타임 라이브러리 함수는 다음 라이브러리에 포함 되어 있습니다.

|OpenMP 런타임 라이브러리|특징|
|------------------------------|---------------------|
|VCOMP. LIB|다중 스레드, 동적 링크 (VCOMP140.DLL에 대 한 가져오기 라이브러리)|
|VCOMPD. LIB|다중 스레드, 동적 링크 (VCOMP140D.DLL에 대 한 가져오기 라이브러리) (디버그)|

_DEBUG이 컴파일에서 정의 되 고 `#include <omp.h>` 가 소스 코드에 있는 경우 VCOMPD입니다. LIB는 기본 lib가 됩니다 (그렇지 않은 경우 VCOMP). LIB가 사용 됩니다.

[/Nodefaultlib (라이브러리 무시)](../../../build/reference/nodefaultlib-ignore-libraries.md) 를 사용 하 여 기본 lib를 제거 하 고 원하는 lib와 명시적으로 연결할 수 있습니다.

OpenMP Dll은 Visual C++ 재배포 가능 디렉터리에 있으며 OpenMP를 사용 하는 응용 프로그램과 함께 배포 해야 합니다.

## <a name="see-also"></a>참고 항목

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)
