---
description: '자세한 정보: 심각한 오류 C1853'
title: 심각한 오류 C1853
ms.date: 11/04/2016
f1_keywords:
- C1853
helpviewer_keywords:
- C1853
ms.assetid: ceb9b4a5-92bf-4573-8a9f-3109cc7743ce
ms.openlocfilehash: 60c8e254e9bd36f52bddb4d6dce56c987b6c31e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276233"
---
# <a name="fatal-error-c1853"></a>심각한 오류 C1853

> '*filename*' 미리 컴파일된 헤더 파일이 이전 버전의 컴파일러에서 온 것 이거나, 미리 컴파일된 헤더가 c + + 이며 c에서 사용 하 고 있거나 그 반대의 경우입니다.

가능한 원인:

- 미리 컴파일된 헤더가 이전 컴파일러 버전으로 컴파일 되었습니다. 현재 컴파일러를 사용 하 여 헤더를 다시 컴파일하십시오.

- 미리 컴파일된 헤더는 c + + 이며 C에서 사용 하 고 있습니다. [/tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) 컴파일러 옵션 중 하나를 지정 하거나 소스 파일의 접미사를 "c"로 변경 하 여 c에서 사용할 헤더를 다시 컴파일하십시오. 자세한 내용은 [코드를 미리 컴파일하기 위한 두 가지 선택 항목](../../build/creating-precompiled-header-files.md#two-choices-for-precompiling-code)을 참조 하세요.
