---
description: '자세한 정보: assert 함수에서 진단 인쇄'
title: assert 함수에서 진단 인쇄
ms.date: 11/04/2016
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
ms.openlocfilehash: cab4f6dfd2cab7d4b46486a103b39abb6ca17005
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186794"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>assert 함수에서 진단 인쇄

**ANSI 4.2** **assert** 함수에 의해 인쇄되는 진단 및 해당 함수의 종료 동작

**assert** 함수는 진단 메시지를 인쇄하고 식이 false(0)이면 **abort** 루틴을 호출합니다. 진단 메시지의 형식은 다음과 같습니다.

> **Assertion failed**: <em>expression</em> **, file** <em>filename</em> **, line** *linenumber*

여기서 *filename* 은 원본 파일의 이름이며 *linenumber* 는 원본 파일에서 실패한 어설션의 줄 번호입니다. *식* 이 true(0이 아님)이면 어떤 작업도 수행되지 않습니다.

## <a name="see-also"></a>참조

[라이브러리 함수](../c-language/library-functions.md)
