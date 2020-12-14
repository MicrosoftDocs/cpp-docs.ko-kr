---
description: '자세한 정보: EDITBIN 참조'
title: EDITBIN 참조
ms.date: 11/04/2016
f1_keywords:
- editbin
helpviewer_keywords:
- binary data, editing
- object files, modifying
- EDITBIN program
- COFF files, editing
ms.assetid: efdda03b-3dfc-4d31-90e6-caf5b3977914
ms.openlocfilehash: ad211ab85ac00cd716b7c3b8e381a9a448ea04ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201029"
---
# <a name="editbin-reference"></a>EDITBIN 참조

Microsoft COFF 이진 파일 편집기 (EDITBIN.EXE)는 COFF (Common Object File Format) 이진 파일을 수정 합니다. EDITBIN을 사용 하 여 개체 파일, 실행 파일 및 DLL (동적 연결 라이브러리)을 수정할 수 있습니다.

> [!NOTE]
> 이 도구는 Visual Studio 명령 프롬프트 에서만 시작할 수 있습니다. 시스템 명령 프롬프트 또는 파일 탐색기에서는 시작할 수 없습니다.

[/Gl](gl-whole-program-optimization.md) 컴파일러 옵션으로 생성 된 파일에는 EDITBIN을 사용할 수 없습니다. /GL로 생성 된 이진 파일에 대 한 모든 수정 작업은 다시 컴파일 및 연결을 통해 수행 해야 합니다.

- [EDITBIN 명령줄](editbin-command-line.md)

- [EDITBIN 옵션](editbin-options.md)

## <a name="see-also"></a>참고 항목

[추가 MSVC 빌드 도구](c-cpp-build-tools.md)
