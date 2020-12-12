---
description: '자세히 알아보기: abort 사용'
title: abort 사용
ms.date: 11/04/2016
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
ms.openlocfilehash: 16c1df7a7b3a26be444d9b17d370366b1a41ea1f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116862"
---
# <a name="using-abort"></a>abort 사용

[Abort](../c-runtime-library/reference/abort.md) 함수를 호출 하면 즉시 종료 됩니다. 이 함수는 초기화된 전역 정적 개체에 대한 일반적인 소멸 프로세스를 건너뜁니다. 또한 이 함수는 `atexit` 함수를 사용하여 지정된 모든 특수 처리를 건너뜁니다.

## <a name="see-also"></a>참고 항목

[추가 종료 고려 사항](../cpp/additional-termination-considerations.md)
