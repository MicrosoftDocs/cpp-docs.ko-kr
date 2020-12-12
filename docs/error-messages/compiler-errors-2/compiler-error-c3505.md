---
description: '자세한 정보: 컴파일러 오류 C3505'
title: 컴파일러 오류 C3505
ms.date: 11/04/2016
f1_keywords:
- C3505
helpviewer_keywords:
- C3505
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
ms.openlocfilehash: 10727b04ce587eb56872440ad7d46dd544eb0642
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113115"
---
# <a name="compiler-error-c3505"></a>컴파일러 오류 C3505

> '*guid*' 형식 라이브러리를 로드할 수 없습니다.

C3505는 64 비트 컴퓨터 64에서 32 비트, x86 호스트 크로스 컴파일러를 실행 하는 경우에 발생할 수 있습니다. 컴파일러는 w o w 64에서 실행 되 고 32 비트 레지스트리 하이브에만 읽을 수 있기 때문입니다.

가져오기를 시도 하는 형식 라이브러리의 32 비트 및 64 비트 버전을 모두 빌드하여이 오류를 해결할 수 있습니다.  또는 기본 64 비트 컴파일러를 사용할 수 있습니다 .이 컴파일러는 64 비트 컴파일러를 가리키도록 IDE에서 **VC + + 디렉터리** 속성을 변경 해야 합니다.

자세한 내용은 다음 항목을 참조하세요.

- [방법: 명령줄에서 64비트 Visual C++ 도구 집합 활성화](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)

- [방법: 64비트, x64 플랫폼을 대상으로 한 Visual C++ 프로젝트 구성](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)
