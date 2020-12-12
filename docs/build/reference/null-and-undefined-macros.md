---
description: '자세히 알아보기: Null 및 정의 되지 않은 매크로'
title: null 및 정의되지 않은 매크로
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, undefined macros
- Null macros in NMAKE
- macros, null and undefined
- undefined macros and NMAKE
- NMAKE program, null macros
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
ms.openlocfilehash: 639afda727f1ebb1f4d7d602ed7cf01d6c914a33
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209726"
---
# <a name="null-and-undefined-macros"></a>null 및 정의되지 않은 매크로

Null 및 정의 되지 않은 매크로는 모두 null 문자열로 확장 되지만 null 문자열로 정의 된 매크로는 전처리 식에 정의 된 것으로 간주 됩니다. 매크로를 null 문자열로 정의 하려면 명령줄 또는 명령 파일에서 등호 (=) 뒤에 공백이 나 탭을 제외한 문자를 지정 하 고 null 문자열 또는 정의를 큰따옴표 ("")로 묶습니다. 매크로를 정의 하지 않으려면을 사용 합니다 **. UNDEF.** 자세한 내용은 [메이크파일 전처리 지시문](makefile-preprocessing-directives.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[NMAKE 매크로 정의](defining-an-nmake-macro.md)
