---
description: '자세한 정보: 인라인 어셈블리 최적화'
title: 인라인 어셈블리 최적화
ms.date: 08/30/2018
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
ms.openlocfilehash: 62c4dad85128089cdcf85f4156884747f928338f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122098"
---
# <a name="optimizing-inline-assembly"></a>인라인 어셈블리 최적화

**Microsoft 전용**

**`__asm`** 함수에 블록이 있으면 여러 가지 방법으로 최적화에 영향을 줍니다. 첫째, 컴파일러는 블록 자체를 최적화 하려고 시도 하지 않습니다 **`__asm`** . 어셈블리 언어로 작성한 내용대로 결과가 발생합니다. 둘째, 블록의 존재는 **`__asm`** 레지스터 변수 저장소에 영향을 줍니다. 컴파일러는 **`__asm`** 레지스터의 내용이 블록에 의해 변경 되는 경우 블록에서 등록 변수를 방지 **`__asm`** 합니다. 마지막으로, 함수에 어셈블리 언어를 포함하면 일부 다른 함수 차원의 최적화에 영향을 줍니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[인라인 어셈블러](../../assembler/inline/inline-assembler.md)<br/>
