---
title: '#오류 지시문 (C/c + +)'
ms.date: 11/04/2016
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
ms.openlocfilehash: c83fc7ef8135ee0cba37a956df47bcab0f796007
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447816"
---
# <a name="error-directive-cc"></a>#error 지시문 (C/C++)
**#error** 지시문은 컴파일 타임에 사용자 지정 오류 메시지를 내보낸 다음 컴파일을 종료합니다.

## <a name="syntax"></a>구문

```
#errortoken-string
```

## <a name="remarks"></a>설명

이 지시문이 생성하는 오류 메시지에는 *token-string* 매개 변수가 포함되어 있습니다. *token-string* 매개 변수는 매크로 확장이 되지 않습니다. 이 명령어는 프로그램 불일치나 제약 조건 위반을 개발자에게 고지하기 위하여 전처리를 하는 동안 가장 유용합니다. 다음 예제에서는 전처리하는 동안의 오류 처리를 보여 줍니다.

```
#if !defined(__cplusplus)
#error C++ compiler required.
#endif
```

## <a name="see-also"></a>참고 항목

[전처리기 지시문](../preprocessor/preprocessor-directives.md)