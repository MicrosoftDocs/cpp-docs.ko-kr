---
title: 와일드카드 인수 확장
description: 링커 옵션을 사용하여 와일드카드 명령줄 인수를 처리하는 방법을 알아봅니다.
ms.date: 11/20/2020
helpviewer_keywords:
- asterisk wildcard
- question mark, wildcard
- expanding wildcard arguments
- wildcards, expanding
ms.openlocfilehash: b847a5dd8af577a4e30edcd9bc7fc34add296c17
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483310"
---
# <a name="expanding-wildcard-arguments"></a>와일드카드 인수 확장

와일드카드 인수 확장은 Microsoft 전용 확장입니다.

C 프로그램을 실행할 때 물음표( **`?`** )와 별표( **`*`** ) 중 하나를 와일드카드로 사용하여 명령줄에서 파일 이름 및 경로 인수를 지정할 수 있습니다.

기본적으로 명령줄 인수에서는 와일드카드가 확장되지 않습니다. 일반 인수 벡터 `argv` 로드 루틴을 *`setargv.obj`* 또는 *`wsetargv.obj`* 파일과 연결하여 와일드카드를 확장하는 버전으로 바꿀 수 있습니다. 프로그램에서 `main` 함수를 사용하는 경우 *`setargv.obj`* 와 연결합니다. 프로그램에서 `wmain` 함수를 사용하는 경우 *`wsetargv.obj`* 와 연결합니다. 이 두 동작은 동일한 동작입니다. 

*`setargv.obj`* 또는 *`wsetargv.obj`* 와 연결하려면 **`/link`** 옵션을 사용합니다. 예를 들면 다음과 같습니다.

**`cl example.c /link setargv.obj`**

운영 체제 명령과 같은 방식으로 와일드카드가 확장됩니다.

## <a name="see-also"></a>참조

[링크 옵션](../c-runtime-library/link-options.md)\
[`main` 함수 및 프로그램 실행](../c-language/main-function-and-program-execution.md)
