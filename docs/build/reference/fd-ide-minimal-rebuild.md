---
title: /FD(IDE 최소 재빌드)
ms.date: 11/04/2016
f1_keywords:
- /FD
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
ms.openlocfilehash: a902096bf13105e6a6a66b7bd3ccc56b8f7cf624
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50433594"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD(IDE 최소 재빌드)

**/FD** 제외 하 고 사용자에 게 노출 되지 합니다 [명령줄](../../ide/command-line-property-pages.md) c + + 프로젝트의 속성 페이지 **속성 페이지** 경우에 대화 상자의 [/Gm (최소 다시 빌드 사용)](../../build/reference/gm-enable-minimal-rebuild.md) 도 선택 하지 않습니다. **/FD** 개발 환경에서 다른 효과가 있습니다. **/FD** 의 출력에 표시 되지 않습니다 **cl /?** 합니다.

사용 하지 않는 경우 **/Gm** 개발 환경의 **/FD** 사용 됩니다. **/FD** .idb 파일에 충분 한 종속성 정보가 있는지 확인 합니다. **/FD** 개발 환경 에서만 사용 되는 명령줄 또는 빌드 스크립트에서 사용 해야 합니다.

## <a name="see-also"></a>참고 항목

[출력 파일(/F) 옵션](../../build/reference/output-file-f-options.md)<br/>
[컴파일러 옵션](../../build/reference/compiler-options.md)<br/>
[컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)