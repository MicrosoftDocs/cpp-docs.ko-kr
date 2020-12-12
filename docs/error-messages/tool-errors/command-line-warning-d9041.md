---
description: 자세한 내용은 Command-Line Warning D9041을 (를) 확인 하세요.
title: 명령줄 경고 D9041
ms.date: 11/04/2016
f1_keywords:
- D9041
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
ms.openlocfilehash: d6226d4e5dd89176c0ed3722a9fd24e1244cacac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119764"
---
# <a name="command-line-warning-d9041"></a>명령줄 경고 D9041

> '/*option-name*'의 '*option-value*' 값이 잘못 되었습니다. '*가정-값*' 이라고 가정 합니다. 이 경고를 지정 하는 경우 명령줄 옵션에 '/analyze '를 추가 합니다.

**`/wd`** **`/we`** **`/wo`** **`/wl`** 명령줄 옵션을 지정 하지 않고,, 또는 명령줄 옵션에 코드 분석 경고 번호가 추가 되었습니다 **`/analyze`** . 이 오류를 해결 하려면 **`/analyze`** 명령줄 옵션을 추가 하거나 적절 한 명령줄 옵션에서 잘못 된 경고 번호를 제거 **`/w`** 합니다.

## <a name="example"></a>예제

다음 명령줄 예제에서는 D9041 경고를 생성 합니다.

```cmd
cl /EHsc /LD /wd6001 filename.cpp
```

이 경고를 해결 하려면 명령줄 옵션을 추가 합니다 **`/analyze`** . **`/analyze`** 버전의 컴파일러에서가 지원 되지 않는 경우 옵션에서 잘못 된 경고 번호를 제거 **`/wd`** 합니다.

## <a name="see-also"></a>참고 항목

[명령줄 오류(D8000~D9999)](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[MSVC 컴파일러 옵션](../../build/reference/compiler-options.md)
