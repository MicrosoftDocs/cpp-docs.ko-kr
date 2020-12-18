---
description: '자세한 정보: 릴리스 빌드를 만들 때의 일반적인 문제'
title: 릴리스 빌드를 만들 때의 일반적인 문제
ms.date: 11/04/2016
helpviewer_keywords:
- unexpected code generation
- debugging [MFC], release builds
- release builds, troubleshooting
- stray pointers
- debug builds, difference from release builds
- MFC [C++], release builds
- heap layout problems
- pointers, stray
- release builds, building applications
- debug memory allocator
- optimization [C++], compiler
- projects [C++], debug configuration
- troubleshooting release builds
- memory [C++], overwrites
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
ms.openlocfilehash: 7470b87a33b9dc0cb6f7e85b9cfa7b7c1216a936
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163095"
---
# <a name="common-problems-when-creating-a-release-build"></a>릴리스 빌드를 만들 때의 일반적인 문제

개발 과정에서는 일반적으로 프로젝트의 디버그 빌드를 사용하여 빌드하고 테스트합니다. 그런 다음 릴리스 빌드용 애플리케이션을 빌드하면 액세스 위반이 발생할 수 있습니다.

아래 목록은 디버그 빌드와 릴리스(비 디버그) 빌드 간의 주요 차이점을 보여 줍니다. 다른 차이점이 있지만, 다음은 애플리케이션이 디버그 빌드에서는 작동하고 릴리스 빌드에서는 실패하게 되는 주요 차이점입니다.

- [힙 레이아웃](#_core_heap_layout)

- [컴파일](#_core_compilation)

- [포인터 지원](#_core_pointer_support)

- [최적화](#_core_optimizations)

디버그 빌드에서 릴리스 빌드 오류를 catch하는 방법에 대한 자세한 내용은 [/GZ(디버그 빌드에서 릴리스 빌드 오류 Catch)](reference/gz-enable-stack-frame-run-time-error-checking.md) 컴파일러 옵션을 참조하세요.

## <a name="heap-layout"></a><a name="_core_heap_layout"></a> 힙 레이아웃

애플리케이션이 디버그 빌드에서는 작동하지만 릴리스 빌드에서는 작동하지 않는 경우 힙 레이아웃이 문제의 원인 중 약 90%를 차지합니다.

프로젝트를 디버그용으로 빌드할 때는 디버그 메모리 할당자를 사용합니다. 즉, 모든 메모리 할당 주위에 가드 바이트가 배치됩니다. 이러한 가드 바이트는 메모리 덮어쓰기를 검색합니다. 힙 레이아웃은 릴리스 버전과 디버그 버전 간에 다르므로 메모리 덮어쓰기가 디버그 빌드에서 문제를 만들지 않을 수 있지만 릴리스 빌드에서 심각한 영향을 미칠 수 있습니다.

자세한 내용은 [메모리 덮어쓰기 확인](checking-for-memory-overwrites.md) 및 [디버그 빌드를 사용하여 메모리 덮어쓰기 확인](using-the-debug-build-to-check-for-memory-overwrite.md)을 참조하세요.

## <a name="compilation"></a><a name="_core_compilation"></a> 컴파일

릴리스용으로 빌드할 때 많은 MFC 매크로와 대부분의 MFC 구현이 변경됩니다. 특히 ASSERT 매크로는 릴리스 빌드에서 nothing으로 평가되므로 ASSERT에 있는 코드는 실행되지 않습니다. 자세한 내용은 [ASSERT 문 검사](using-verify-instead-of-assert.md)를 참조하세요.

일부 함수는 릴리스 빌드에서 속도를 개선하기 위해 인라인 처리됩니다. 릴리스 빌드에서는 일반적으로 최적화가 사용됩니다. 다른 메모리 할당자도 사용됩니다.

## <a name="pointer-support"></a><a name="_core_pointer_support"></a> 포인터 지원

디버깅 정보가 없으면 애플리케이션에서 패딩이 제거됩니다. 릴리스 빌드에서는 스트레이 포인터가 디버그 정보를 가리키는 대신 초기화되지 않은 메모리를 가리킬 가능성이 높습니다.

## <a name="optimizations"></a><a name="_core_optimizations"></a> 최적화

특정 코드 세그먼트의 특성에 따라 최적화 컴파일러는 예기치 않은 코드를 생성할 수 있습니다. 이는 릴리스 빌드 문제 중 가장 가능성이 낮은 원인이지만 때때로 발생합니다. 해결 방법은 [코드 최적화](optimizing-your-code.md)를 참조하세요.

## <a name="see-also"></a>참조

[릴리스 빌드](release-builds.md)<br/>
[릴리스 빌드 문제 해결](fixing-release-build-problems.md)
