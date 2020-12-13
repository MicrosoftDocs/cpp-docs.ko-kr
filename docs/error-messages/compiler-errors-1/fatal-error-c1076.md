---
description: '자세한 정보: 심각한 오류 C1076'
title: 심각한 오류 C1076
ms.date: 03/08/2019
f1_keywords:
- C1076
helpviewer_keywords:
- C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
ms.openlocfilehash: 2d2ca5ffc8970affa6ddd01011e1a37c7b5b778d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341804"
---
# <a name="fatal-error-c1076"></a>심각한 오류 C1076

> 컴파일러 한계 : 내부 힙 한계에 도달했습니다. /Zm을 사용하여 한계를 더 높게 지정하십시오.

템플릿 인스턴스화나 기호가 너무 많은 경우 이 오류가 발생할 수 있습니다. Visual Studio 2015부터이 메시지는 너무 많은 병렬 빌드 프로세스로 인 한 Windows 가상 메모리 압력으로 인해 발생할 수 있습니다. 이 경우에는 지시어를 사용 하는 경우를 제외 하 고 **/zm** 옵션을 사용 하는 것이 좋습니다 `#pragma hdrstop` .

이 오류를 해결하려면

1. 미리 컴파일된 헤더에서 지시문을 사용 하는 경우 `#pragma hdrstop` [/zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) 옵션을 사용 하 여 컴파일러 메모리 제한을 [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) 오류 메시지에 지정 된 값으로 설정 합니다. Visual Studio에서이 값을 설정 하는 방법을 포함 하는 자세한 내용은 [/zm (미리 컴파일된 헤더 메모리 할당 제한 지정)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)의 설명 섹션을 참조 하세요.

1. **/Maxcpucount** 옵션을 사용 하 여 지정 된 병렬 프로세스의 수를 **/mp** 옵션과 함께 CL.EXE 하 MSBUILD.EXE 하는 것이 좋습니다. 자세한 내용은 [미리 컴파일된 헤더 (PCH) 문제 및 권장 사항](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/)을 참조 하세요.

1. 64비트 운영 체제에서 32비트로 호스팅된 컴파일러를 사용하는 경우 64비트로 호스팅된 컴파일러를 대신 사용하십시오. 자세한 내용은 [방법: 명령줄에서 64 비트 Visual C++ 도구 집합 사용](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)을 참조 하세요.

1. 필요 없는 포함 파일을 제거합니다.

1. 예를 들어, 대형 배열을 선언하는 대신에 메모리를 동적으로 할당하여 필요 없는 전역 변수를 제거합니다.

1. 사용되지 않는 선언을 제거합니다.

빌드가 시작 된 직후에 C1076이 발생 하면 프로그램에 대해 **/zm** 에 지정 된 값이 너무 높을 수 있습니다. **/Zm** 값을 줄입니다.
