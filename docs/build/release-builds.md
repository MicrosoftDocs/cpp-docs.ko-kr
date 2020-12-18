---
description: '자세한 정보: 릴리스 빌드'
title: C++ 릴리스 빌드 - Visual Studio
ms.date: 12/10/2018
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
ms.openlocfilehash: 7168fd50421835edc82d0599b22deb9214e28869
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273789"
---
# <a name="release-builds"></a>릴리스 빌드

릴리스 빌드는 최적화를 사용합니다. 최적화를 사용하여 릴리스 빌드를 만들 때 컴파일러는 기호화된 디버깅 정보를 생성하지 않습니다. TRACE 및 ASSERT 호출에 대해 코드가 생성되지 않는다는 점에서 기호화된 디버깅 정보가 없을 경우 실행 파일의 크기가 감소하고, 따라서 더 빨라집니다.

## <a name="in-this-section"></a>단원 내용

[릴리스 빌드를 만들 때의 일반적인 문제](common-problems-when-creating-a-release-build.md)<br/>
[릴리스 빌드 문제 해결](fixing-release-build-problems.md)<br/>
[ASSERT 대신 VERIFY 사용](using-verify-instead-of-assert.md)<br/>
[디버그 빌드를 사용한 메모리 덮어쓰기 확인](using-the-debug-build-to-check-for-memory-overwrite.md)<br/>
[방법: 릴리스 빌드 디버그](how-to-debug-a-release-build.md)<br/>
[메모리 덮어쓰기 확인](checking-for-memory-overwrites.md)<br/>
[코드 최적화](optimizing-your-code.md)

## <a name="see-also"></a>참조

[C/C++ 빌드 참조](reference/c-cpp-building-reference.md)
