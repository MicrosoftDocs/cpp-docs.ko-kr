---
description: '자세한 정보: NMAKE 심각한 오류 U1033'
title: NMAKE 심각한 오류 U1033
ms.date: 11/04/2016
f1_keywords:
- U1033
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
ms.openlocfilehash: e616e98a21c92137fab4b167318a9305a2175bb2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272138"
---
# <a name="nmake-fatal-error-u1033"></a>NMAKE 심각한 오류 U1033

구문 오류: 예기치 않은 ' string '입니다.

문자열은 메이크파일의 올바른 구문의 일부가 아닙니다.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>다음과 같은 가능한 원인을 확인하여 수정하려면

1. 인라인 파일의 닫는 꺾쇠 괄호 ( **<<** ) 집합이 줄의 시작 부분에 없으면 다음 오류가 발생 합니다.

    ```
    syntax error : 'EOF' unexpected
    ```

1. 메이크파일의 매크로 정의에 앞의 이름 없이 등호 ()가 포함 되어 **=** 있거나 정의 되는 이름이 nothing으로 확장 되는 매크로 인 경우 다음 오류가 발생 합니다.

    ```
    syntax error : '=' unexpected
    ```

1. TOOLS.INI의 주석 줄에 있는 세미콜론 (**;**)이 줄의 시작 부분에 없으면 다음 오류가 발생 합니다.

    ```
    syntax error : ';' unexpected
    ```

1. Word 프로세서에서 메이크파일의 형식이 지정 된 경우 다음 오류가 발생할 수 있습니다.

    ```
    syntax error : ':' unexpected
    ```
