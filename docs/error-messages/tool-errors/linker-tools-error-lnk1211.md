---
description: '자세한 정보: 링커 도구 오류 LNK1211'
title: 링커 도구 오류 LNK1211
ms.date: 12/05/2017
f1_keywords:
- LNK1211
helpviewer_keywords:
- LNK1211
ms.assetid: 607400eb-4180-4892-817f-eedfa628af61
ms.openlocfilehash: d3201055643f5874ccc319f04fb6eb2d976bf67f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341622"
---
# <a name="linker-tools-error-lnk1211"></a>링커 도구 오류 LNK1211

> 미리 컴파일된 형식 정보를 찾을 수 없습니다. '*filename*'은 (는) 연결 되지 않았거나 덮어 쓰여졌습니다.

[/Yc](../../build/reference/yc-create-precompiled-header-file.md)를 사용 하 여 컴파일한 *파일 이름* 개체 파일이 LINK 명령에 지정 되지 않았거나 덮어쓰여집니다.

미리 컴파일된 헤더를 사용 하는 디버그 라이브러리를 만들고 **/yc** 및 [/z7](../../build/reference/z7-zi-zi-debug-information-format.md)을 지정 하는 경우 Visual C++는 디버그 정보를 포함 하는 미리 컴파일된 개체 파일을 생성 합니다. 이 오류는 미리 컴파일된 개체 파일을 라이브러리에 저장 하 고, 라이브러리를 사용 하 여 실행 가능한 이미지를 빌드하고, 참조 된 개체 파일에 미리 컴파일된 개체 파일이 정의 하는 함수에 대 한 전이적 참조가 없는 경우에만 발생 합니다.

이러한 상황을 해결 하는 방법에는 다음 두 가지가 있습니다.

- [/Yd](../../build/reference/yd-place-debug-information-in-object-file.md) 컴파일러 옵션을 지정 하 여 미리 컴파일된 헤더의 디버그 정보를 각 개체 모듈에 추가 합니다. 이 방법은 일반적으로 응용 프로그램을 연결 하는 데 필요한 시간을 늘릴 수 있는 작은 개체 모듈을 생성 하기 때문에 바람직하지 않습니다.

- 함수 정의를 포함 하지 않는 미리 컴파일된 헤더 파일을 만들 때 [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) 를 지정 하 고 임의의 문자열 이름을 전달 합니다. 그러면 컴파일러가 미리 컴파일된 개체 파일에 기호를 만들고 미리 컴파일된 개체 파일에 연결 된 미리 컴파일된 헤더 파일을 사용 하는 각 개체 파일에서 해당 기호에 대 한 참조를 내보내도록 지시 합니다.

**/Yc** 및 **/Yl** 를 사용 하 여 모듈을 컴파일할 때 컴파일러는와 비슷한 기호를 만듭니다. `__@@_PchSym_@00@...@symbol_name` 여기서 줄임표 (...)는 컴파일러에서 생성 된 문자열을 나타내고 개체 모듈에 저장 합니다. 이 미리 컴파일된 헤더를 사용 하 여 컴파일하는 모든 소스 파일은 지정 된 기호를 참조 합니다. 그러면 링커에서는 개체 모듈과 해당 디버깅 정보를 라이브러리에서 포함 합니다.
