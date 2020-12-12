---
description: '자세히 알아보기: 주석 (c + +)'
title: 주석(C++)
ms.date: 11/04/2016
helpviewer_keywords:
- code comments, C++
- comments, documenting code
- comments, C++ code
- white space, C++ comments
ms.assetid: 6fcb906c-c264-4083-84bc-373800b2e514
ms.openlocfilehash: b3bbcafe1f18c791fc5935161b6cdbfae0bf03cf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239794"
---
# <a name="comments-c"></a>주석(C++)

주석은 컴파일러가 무시 하지만 프로그래머에 게 유용한 텍스트입니다. 주석은 나중에 참조할 수 있도록 코드에 주석을 추가 하는 데 일반적으로 사용 됩니다. 컴파일러는이를 공백으로 처리 합니다. 테스트에 주석을 사용 하 여 특정 코드 줄을 비활성 상태로 만들 수 있습니다. 그러나 `#if` / `#endif` 주석을 포함 하는 코드를 감쌀 수는 있지만 주석을 중첩할 수 없기 때문에 전처리기 지시문은이 작업을 수행 하는 데 더 효과적입니다.

C + + 주석은 다음 중 한 가지 방법으로 작성 됩니다.

- `/*`(슬래시, 별표) 문자 뒤에 문자 (새 줄 포함)와 문자를 차례로 입력 합니다 `*/` . 이 구문은 ANSI C와 동일 합니다.

- `//`(두 개의 슬래시) 문자 뒤에 문자 시퀀스가 나옵니다. 백슬래시가 바로 앞에 오지 않는 새 줄은이 주석 형태를 종료 합니다. 따라서 일반적으로 "한 줄로 된 주석" 이라고 합니다.

주석 문자 ( `/*` , `*/` 및)는 `//` 문자 상수, 문자열 리터럴 또는 주석 내에서 특별 한 의미가 없습니다. 따라서 첫 번째 구문을 사용 하는 주석은 중첩할 수 없습니다.

## <a name="see-also"></a>참고 항목

[어휘 규칙](../cpp/lexical-conventions.md)
