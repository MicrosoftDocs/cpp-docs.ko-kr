---
title: setlocale pragma
ms.date: 08/29/2019
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
ms.openlocfilehash: 219354595e5c63b2f13211d43bfa517d97413251
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218167"
---
# <a name="setlocale-pragma"></a>setlocale pragma

와이드 문자 상수와 문자열 리터럴을 변환할 때 사용할 *로캘*, 국가, 지역 및 언어를 정의 합니다.

## <a name="syntax"></a>구문

> **#pragma setlocale ("** [ *locale-string* ] **")**

## <a name="remarks"></a>설명

멀티 바이트 문자를 와이드 문자로 변환 하는 알고리즘은 로캘에 따라 다를 수 있으며 실행 파일이 실행 되는 다른 로캘에서 컴파일이 발생할 수 있습니다 .이 pragma는 컴파일 시간에 대상 로캘을 지정 하는 방법을 제공 합니다. 와이드 문자 문자열은 올바른 형식으로 저장 됩니다.

기본 *로캘 문자열* 은 ""입니다.

"C" 로캘은 문자열의 각 문자를 **wchar_t**로 해당 값에 매핑합니다. 에 `setlocale` 유효한 다른 값은 [언어 문자열](../c-runtime-library/language-strings.md) 목록에 있는 항목입니다. 예를 들어 다음과 같이 지정할 수 있습니다.

```cpp
#pragma setlocale("dutch")
```

언어 문자열을 지정 하는 기능은 컴퓨터의 코드 페이지 및 언어 ID 지원에 따라 달라 집니다.

## <a name="see-also"></a>참고자료

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
