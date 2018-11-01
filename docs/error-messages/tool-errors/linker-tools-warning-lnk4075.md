---
title: 링커 도구 경고 LNK4075
ms.date: 11/04/2016
f1_keywords:
- LNK4075
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
ms.openlocfilehash: bba0fa85a3f2590c84cbb6f78fac7e49386d35a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548254"
---
# <a name="linker-tools-warning-lnk4075"></a>링커 도구 경고 LNK4075

"option1" "option2" 사양으로 인해 무시 됩니다.

두 번째 옵션에는 첫 번째를 재정의합니다.

상호 배타적인 링커 옵션 지정 됩니다.  링커 옵션을 확인 합니다.  링커 옵션을 지정 하는 프로젝트를 빌드하는 방법에 따라 달라 집니다.

- 개발 환경에서 작성 하는 경우 프로젝트에 대 한 링커 속성 페이지의 모양과 링커 옵션을 모두 지정 된 위치를 참조 하세요.  참조 [프로젝트 속성 작업](../../ide/working-with-project-properties.md) 자세한 내용은 합니다.

- 명령줄에서 빌드하는 경우 지정 된 링커 옵션을 확인 합니다.

- 빌드 스크립트를 사용 하 여 작성 하는 경우에 해당 링커 옵션이 지정 된 위치를 확인 하려면 스크립트를 확인 합니다.

상호 배타적인 링커 옵션을 지정 하는 위치를 찾으면 링커 옵션 중 하나를 제거 합니다.

몇 가지 예제.

- 으로 컴파일된 모듈을 연결 하면 **/ZI**를 하면 의미 없는 /EDITANDCONTINUE /EDITANDCONTINUE, 및 /opt: ref, /opt: icf, /incremental: no를 사용 하 여 컴파일된 모듈 호출 즉 내부 링커 옵션 LNK4075를 가져옵니다.  참조 [/z7, /Zi, /ZI (디버그 정보 형식)](../../build/reference/z7-zi-zi-debug-information-format.md) 자세한 내용은 합니다.