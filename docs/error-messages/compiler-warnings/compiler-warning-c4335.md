---
description: '자세한 정보: 컴파일러 경고 C4335'
title: 컴파일러 경고 C4335
ms.date: 11/04/2016
f1_keywords:
- C4335
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
ms.openlocfilehash: fc8f86036a299c41bc0cb1814b98372edc3b4d8f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238312"
---
# <a name="compiler-warning-c4335"></a>컴파일러 경고 C4335

Mac 파일 형식이 검색 됨: 원본 파일을 DOS 또는 UNIX 형식으로 변환 하세요.

소스 파일의 첫 번째 줄에 있는 줄 끝 문자는 UNIX (' \n ') 또는 DOS (' \r\n ')와는 달리 Macintosh 스타일 (' \r ')입니다.

이 경고는 항상 오류로 실행 됩니다.  이 경고를 사용 하지 않도록 설정 하는 방법에 대 한 자세한 내용은 [warning](../../preprocessor/warning.md) pragma를 참조 하십시오.  또한이 경고는 compiland 당 한 번만 실행 됩니다. 따라서 `#include` Macintosh 형식으로 파일을 지정 하는 지시문이 여러 개 있는 경우 C4335은 한 번만 실행 됩니다.

Macintosh 형식으로 파일을 생성 하는 한 가지 방법은 Visual Studio의 **파일** 메뉴에서 **고급 저장 옵션** 을 사용 하는 것입니다.

## <a name="example"></a>예제

다음 샘플에서는 C4335를 생성 합니다.

```cpp
// C4335 expected
#include "c4335.h"   // assume both include files are in Macintosh format
#include "c4335_2.h"
```
