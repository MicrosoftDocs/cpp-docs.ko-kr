---
description: '자세한 정보: 링커 도구 경고 LNK4075'
title: 링커 도구 경고 LNK4075
ms.date: 11/04/2016
f1_keywords:
- LNK4075
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
ms.openlocfilehash: d7883573271522857b34b3aac81bf45029e540ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210155"
---
# <a name="linker-tools-warning-lnk4075"></a>링커 도구 경고 LNK4075

"옵션 2 마이그레이션" 사양 때문에 "옵션 1 마이그레이션"를 무시 합니다.

두 번째 옵션은 첫 번째 옵션을 재정의 합니다.

상호 배타적인 링커 옵션을 지정 하 고 있습니다.  링커 옵션을 검사 합니다.  링커 옵션이 지정 되는 위치는 프로젝트를 빌드하는 방법에 따라 달라 집니다.

- 개발 환경에서 빌드하는 경우 프로젝트에 대 한 링커 속성 페이지에서 두 링커 옵션이 지정 된 위치를 확인 합니다.  자세한 내용은 [컴파일러 및 빌드 속성 설정](../../build/working-with-project-properties.md) 을 참조 하세요.

- 명령줄에서 빌드하는 경우 여기에 지정 된 링커 옵션을 확인 합니다.

- 빌드 스크립트를 사용 하 여 빌드하는 경우 스크립트를 살펴보면 이러한 링커 옵션이 지정 되는 위치를 확인할 수 있습니다.

상호 배타적인 링커 옵션이 지정 된 위치를 찾았으면 링커 옵션 중 하나를 제거 합니다.

몇 가지 구체적인 예는 다음과 같습니다.

- **/Zi** 를 사용 하 여 컴파일된 모듈을 연결 하는 경우/candcontinue 라는 내부 링커 옵션을 의미 하 고/OPT: REF,/OPT: ICF 또는/INCREMENTAL: no를 사용 하 여 컴파일된 모듈은 LNK4075를 가져옵니다.  자세한 내용은 [/Z7,/zi,/zi (디버그 정보 형식)](../../build/reference/z7-zi-zi-debug-information-format.md) 를 참조 하세요.
