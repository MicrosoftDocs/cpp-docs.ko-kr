﻿---
title: /FD(IDE 최소 재빌드)
ms.date: 04/08/2019
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: 896adcb97a259e6714cf23241424841456371491
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439811"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD(IDE 최소 재빌드)

**/Fd** 는 C++ 프로젝트의 **속성 페이지** 대화 상자 [에 있는 명령줄 속성 페이지](command-line-property-pages.md) 에서 사용자 에게만 노출 됩니다. 사용 되지 않는 및 기본 [/gm (최소 다시 빌드 사용)](gm-enable-minimal-rebuild.md) 옵션을 선택 하지 않은 경우에만 사용할 수 있습니다. **/Fd** 는 개발 환경에서의 영향을 받지 않습니다. **/Fd** 는 `cl /?`출력에 표시 되지 않습니다.

개발 환경에서 사용 되지 않는 **/gm** 옵션을 사용 하도록 설정 하지 않으면 **/fd** 가 사용 됩니다. **/Fd** 는 .idb 파일에 충분 한 종속성 정보가 있는지 확인 합니다. **/Fd** 는 개발 환경 에서만 사용 되며 명령줄 또는 빌드 스크립트에서 사용할 수 없습니다.

## <a name="see-also"></a>참고 항목

[출력 파일(/F) 옵션](output-file-f-options.md)<br/>
[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)
