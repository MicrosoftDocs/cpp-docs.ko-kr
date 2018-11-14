---
title: 구현 정의 동작
ms.date: 11/04/2016
helpviewer_keywords:
- Visual C, portability of Microsoft C
- portability [C++], Microsoft C to ANSI C
- ANSI [C++], C standard
- implementation-defined behavior
ms.assetid: c9f50670-23cb-401f-8ad7-136972012eb9
ms.openlocfilehash: e74d4bceee722ced42ccf63e89fe8ad2a4b866e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447101"
---
# <a name="implementation-defined-behavior"></a>구현 정의 동작

ANSI X3.159-1989, *American National Standard for Information Systems* - *프로그래밍 언어* - *C*에는 "이식성 문제"라는 섹션이 포함되어 있습니다. 이 ANSI 섹션에는 ANSI에서 각각의 특정 구현에 열어 놓은 C 언어의 영역이 나열되어 있습니다. 이 단원에서는 Microsoft C에서 이러한 구현 시 정의되는 C 언어의 영역을 처리하는 방식을 설명합니다.

이 단원은 ANSI 섹션과 같은 순서를 따릅니다. 설명되는 각 항목에는 구현 시 정의되는 동작을 설명하는 ANSI에 대한 참조가 포함되어 있습니다.

> [!NOTE]
>  이 단원에서는 C 컴파일러의 영어(미국) 버전만 설명합니다. 다른 언어에 대한 Microsoft C 구현은 약간 다를 수 있습니다.

## <a name="see-also"></a>참고 항목

[C# 언어 참조](../c-language/c-language-reference.md)