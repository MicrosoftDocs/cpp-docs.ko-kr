---
title: 종료 처리기 작성 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structured exception handling [C++], termination handlers
- exceptions [C++], terminating
- termination handlers [C++], writing
- handlers [C++]
- handlers [C++], termination
- termination handlers
- exception handling [C++], termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 52aa1f8f-f8dd-44b8-be94-5e2fc88d44fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85241d9dde87e929b02328a6e7d0c75b5ce068ef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116232"
---
# <a name="writing-a-termination-handler"></a>종료 처리기 작성

예외 처리기와 달리 종료 처리기는 보호된 코드 블록이 정상적으로 종료되었는지 여부와 관계없이 항상 실행됩니다. 종료 처리기의 유일한 목적은 코드 섹션의 실행 완료 방법과 관계없이 메모리, 핸들 및 파일과 같은 리소스가 제대로 닫혔는지 확인하는 것이어야 합니다.

종료 처리기는 try-finally 문을 사용합니다.

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [Try-finally 문](../cpp/try-finally-statement.md)

- [리소스 정리](../cpp/cleaning-up-resources.md)

- [예외 처리에서의 작업 타이밍](../cpp/timing-of-exception-handling-a-summary.md)

- [종료 처리기에 대 한 제한](../cpp/restrictions-on-termination-handlers.md)

## <a name="see-also"></a>참고자료

[구조적 예외 처리(C/C++)](../cpp/structured-exception-handling-c-cpp.md)