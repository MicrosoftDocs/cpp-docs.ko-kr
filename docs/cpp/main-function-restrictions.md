---
title: main 함수 제한 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Main
dev_langs:
- C++
helpviewer_keywords:
- main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93f5cce15d4db9f7f6d4e3361d22028fccd676f2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117363"
---
# <a name="main-function-restrictions"></a>main 함수 제한

에 몇 가지 제한 사항이 적용 된 **주** 다른 c + + 함수에 적용 되지 않는 함수입니다. 합니다 **주** 함수:

- 오버 로드할 수 없습니다 (참조 [함수 오버 로드](function-overloading.md)).

- 로 선언할 수 없습니다 **인라인**합니다.

- 로 선언할 수 없습니다 **정적**합니다.

- 주소를 사용할 수 없습니다.

- 호출할 수 없습니다.

## <a name="see-also"></a>참고자료

[main: 프로그램 시작](../cpp/main-program-startup.md)