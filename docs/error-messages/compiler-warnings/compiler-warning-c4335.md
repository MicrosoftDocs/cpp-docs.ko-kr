---
title: 컴파일러 경고 C4335 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4335
dev_langs:
- C++
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2b28909d0c4b663fffeacbec58ad694131bb008
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036581"
---
# <a name="compiler-warning-c4335"></a>컴파일러 경고 C4335

Mac 파일 형식이 발견 되었습니다: 원본 파일을 DOS 나 UNIX 형식으로 변환 하세요

소스 파일의 첫 번째 줄의 줄 종료 문자는 UNIX ('\n') 또는 DOS ('\r\n')와 달리 Macintosh 스타일 ('\r').

이 경고는 항상 오류로 서 발생 합니다.  참조 [경고](../../preprocessor/warning.md) 이 경고를 사용 하지 않도록 설정 하는 방법에 대 한 정보에 대 한 pragma입니다.  또한이 경고가 발생 한 번 compiland 당 합니다. 따라서 여러 개 있을 경우 `#include` 형식 파일을 지정 하는 지시문을 C4335 됩니다 수 한 번만 발생 합니다.

형식에서 파일을 생성 하는 한 가지 방법은 사용 하는 것을 **고급 저장 옵션** (에 **파일** 메뉴) Visual Studio에서.

## <a name="example"></a>예제

다음 샘플 C4335를 생성합니다.

```
// C4335 expected
#include "c4335.h"   // assume both include files are in Macintosh format
#include "c4335_2.h"
```