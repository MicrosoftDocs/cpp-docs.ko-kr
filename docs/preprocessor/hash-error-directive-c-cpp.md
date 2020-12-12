---
description: '자세한 정보: #error 지시문 (C/c + +)'
title: '#error 지시문(C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
ms.openlocfilehash: fd6503de9590893ee0ec53cbbfa59429a0cfdcfe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261153"
---
# <a name="error-directive-cc"></a>#error 지시문 (C/c + +)

**#Error** 지시문은 컴파일 시간에 사용자 지정 오류 메시지를 내보낸 다음 컴파일을 종료 합니다.

## <a name="syntax"></a>Syntax

> **#error** *토큰-문자열*

## <a name="remarks"></a>설명

이 지시문이 내보내는 오류 메시지에는 *토큰 문자열* 매개 변수가 포함 됩니다. *토큰 문자열* 매개 변수에는 매크로 확장이 적용 되지 않습니다. 이 지시어는 프로그램 불일치 또는 제약 조건 위반을 개발자에 게 알리기 위해 전처리 중에 가장 유용 합니다. 다음 예제에서는 전처리 중에 오류 처리를 보여 줍니다.

```cpp
#if !defined(__cplusplus)
#error C++ compiler required.
#endif
```

## <a name="see-also"></a>참고 항목

[전처리기 지시문](../preprocessor/preprocessor-directives.md)
