---
description: '자세한 정보: 심각한 오류 C1383'
title: 심각한 오류 C1383
ms.date: 11/04/2016
f1_keywords:
- C1383
helpviewer_keywords:
- C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
ms.openlocfilehash: df20ac07cb3a6c94ff04b42b48ce23f168bb78c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276506"
---
# <a name="fatal-error-c1383"></a>심각한 오류 C1383

컴파일러 옵션 /GL은 설치된 공용 언어 런타임 버전과 호환되지 않습니다.

최신 컴파일러에서 이전 버전의 공용 언어 런타임을 사용하며 **/clr** 및 **/GL.** 으로 컴파일하는 경우 C1383이 발생합니다.

해결하려면 **/clr** 과 함께 **/GL** 을 사용하지 않거나, 컴파일러와 함께 제공된 공용 언어 런타임 버전을 설치합니다.

자세한 내용은 [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) 및 [/GL (Whole Program Optimization)](../../build/reference/gl-whole-program-optimization.md)를 참조하세요.
