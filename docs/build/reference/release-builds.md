---
title: 릴리스 빌드
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
ms.openlocfilehash: 77e02b424b10b5e9606cc49152c2e21d7eeed9cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667456"
---
# <a name="release-builds"></a>릴리스 빌드

릴리스 빌드에는 최적화를 사용합니다. 최적화를 사용하여 릴리스 빌드를 만들 경우 컴파일러가 기호화된 디버깅 정보를 생성하지 않습니다. 기호화된 디버깅 정보가 없고 TRACE 및 ASSERT 호출에 대한 코드가 생성되지 않으면 실행 파일의 크기가 줄어들고 따라서 속도가 더 빨라지게 됩니다.

이 단원에서는 디버그 빌드에서 릴리스 빌드로 변경하면 좋은 이유 및 시기에 대해 설명합니다. 또한 디버그 빌드에서 릴리스 빌드로 변경할 때 발생할 수 있는 일부 문제점에 대해서도 설명합니다.

- [릴리스 빌드 만들기](../../build/reference/how-to-create-a-release-build.md)

- [릴리스 빌드를 만들 때의 일반적인 문제](../../build/reference/common-problems-when-creating-a-release-build.md)

- [릴리스 빌드 문제 해결](../../build/reference/fixing-release-build-problems.md)

   - [ASSERT 문 검사](../../build/reference/using-verify-instead-of-assert.md)

   - [디버그 빌드를 사용한 메모리 덮어쓰기 확인](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)

   - [릴리스 빌드 디버깅](../../build/reference/how-to-debug-a-release-build.md)

   - [메모리 덮어쓰기 확인](../../build/reference/checking-for-memory-overwrites.md)

## <a name="see-also"></a>참고 항목

[Visual Studio에서 C++ 프로젝트 빌드](../../ide/building-cpp-projects-in-visual-studio.md)<br/>
[C/C++ 빌드 참조](../../build/reference/c-cpp-building-reference.md)
