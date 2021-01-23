---
description: pragmaMicrosoft C/c + +의 detect_mismatch 지시문에 대해 자세히 알아보세요.
title: detect_mismatch pragma
ms.date: 01/22/2021
f1_keywords:
- vc-pragma.detect_mismatch
- detect_mismatch_CPP
helpviewer_keywords:
- pragma, detect_mismatch
- detect_mismatch pragma
no-loc:
- pragma
ms.openlocfilehash: 33bc899eaaed73329e24e7f210fa91adc8addaa9
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713677"
---
# <a name="detect_mismatch-no-locpragma"></a>`detect_mismatch` pragma

레코드를 개체에 배치합니다. 링커는 이러한 레코드를 검사하여 잠재적인 불일치를 확인합니다.

## <a name="syntax"></a>구문

> **`#pragma detect_mismatch(`** "*name*" **`,`** "*value*" **`)`**

## <a name="remarks"></a>설명

프로젝트에 연결 하면 프로젝트에 동일한 *이름의* 두 개체가 포함 되어 있지만 각각 다른 *값* 을 가지는 경우 링커는 [LNK2038](../error-messages/tool-errors/linker-tools-error-lnk2038.md) 오류를 throw 합니다. pragma일관성 없는 개체 파일이 연결 되지 않도록 하려면이를 사용 합니다.

*이름과* *값* 은 모두 문자열 리터럴이 며 이스케이프 문자 및 연결에 대 한 문자열 리터럴에 대 한 규칙을 준수 합니다. 이는 대/소문자를 구분 하며 쉼표, 등호, 따옴표 또는 **null** 문자를 포함할 수 없습니다.

## <a name="example"></a>예제

이 예제에서는 같은 버전 레이블에 대한 버전 번호가 서로 다른 두 파일을 만듭니다.

```cpp
// pragma_directive_detect_mismatch_a.cpp
#pragma detect_mismatch("myLib_version", "9")
int main ()
{
   return 0;
}

// pragma_directive_detect_mismatch_b.cpp
#pragma detect_mismatch("myLib_version", "1")
```

명령줄을 사용 하 여 이러한 파일을 모두 컴파일하는 경우 `cl pragma_directive_detect_mismatch_a.cpp pragma_directive_detect_mismatch_b.cpp` LNK2038 오류가 표시 됩니다.

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
