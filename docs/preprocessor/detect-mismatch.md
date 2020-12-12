---
description: '다음에 대 한 자세한 정보: detect_mismatch pragma'
title: detect_mismatch pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.detect_mismatch
- detect_mismatch_CPP
helpviewer_keywords:
- pragmas, detect_mismatch
- detect_mismatch pragma
ms.assetid: ddb13ac9-0e2f-40ce-be69-7e44c04f5a12
ms.openlocfilehash: e57ffac731409fb14b61d35f780ee19094108655
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300738"
---
# <a name="detect_mismatch-pragma"></a>detect_mismatch pragma

레코드를 개체에 배치합니다. 링커는 이러한 레코드를 검사하여 잠재적인 불일치를 확인합니다.

## <a name="syntax"></a>Syntax

> **#pragma detect_mismatch (** "*name*" **,** "*value*" **)**

## <a name="remarks"></a>설명

프로젝트에 연결 하면 프로젝트에 동일한 *이름의* 두 개체가 포함 되어 있지만 각각 다른 *값* 을 가지는 경우 링커는 [LNK2038](../error-messages/tool-errors/linker-tools-error-lnk2038.md) 오류를 throw 합니다. 이 pragma를 사용하여 일치하지 않는 개체 파일이 링크되는 것을 방지할 수 있습니다.

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

`cl pragma_directive_detect_mismatch_a.cpp pragma_directive_detect_mismatch_b.cpp` 명령줄을 사용하여 이러한 파일을 둘 다 컴파일하는 경우 `LNK2038` 오류가 발생합니다.

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
