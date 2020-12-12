---
description: '자세한 정보: 심각한 오류 C1128'
title: 심각한 오류 C1128
ms.date: 11/04/2016
f1_keywords:
- C1128
helpviewer_keywords:
- C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
ms.openlocfilehash: c63a875df2fa5edca57d6d0c3876c09a30ce1115
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123671"
---
# <a name="fatal-error-c1128"></a>심각한 오류 C1128

섹션 수가 개체 파일 형식 한계를 초과 했습니다./bigobj로 컴파일합니다.

.Obj 파일의 허용 되는 섹션 수 (COFF 개체 파일 형식 제한)를 초과 했습니다.

이 섹션 제한에 도달 하면 [/gy](../../build/reference/gy-enable-function-level-linking.md) 와 디버그 빌드를 사용한 결과일 수 있습니다. **/Gy** 는 함수를 자체 COMDAT 섹션으로 이동 시킵니다. 디버그 빌드에서는 각 COMDAT 함수에 대 한 디버그 정보 섹션이 있습니다.

인라인 함수가 너무 많은 경우에도 C1128 발생할 수 있습니다.

이 오류를 해결 하려면 소스 파일을 여러 소스 코드 파일로 나누고, **/gy** 를 사용 하지 않고 컴파일하거나,/bigobj로 컴파일합니다 [(에서 섹션의 수 늘리기). Obj 파일)](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md).  **/Gy** 로 컴파일하지 않는 경우 **/O2** 와 **/o2** 모두 **/gy** 를 암시 하므로 최적화를 개별적으로 지정 해야 합니다.

가능 하면 디버깅 정보 없이 컴파일합니다.

컴파일러가이를 내보내는 대신 별도의 소스 코드 파일에 템플릿의 특정 인스턴스화가 필요할 수도 있습니다.

코드를 이식할 때 x64 컴파일러를 사용 하는 경우와 x86 컴파일러를 사용 하는 경우에는 C1128가 먼저 나타날 가능성이 높습니다. x 64에는 각 함수에 연결 된 각각의 함수에 4 개 이상의 섹션이 있습니다. 즉, 코드, .pdata 및 디버그 정보, .xdata 등의 템플릿 또는 클래스에서 인라인 된 **/gy** 를 컴파일합니다.  X 86은 .pdata를 갖지 않습니다.
