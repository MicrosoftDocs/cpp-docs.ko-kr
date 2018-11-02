---
title: 프로젝트 빌드 오류 PRJ0050
ms.date: 11/04/2016
f1_keywords:
- PRJ0050
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
ms.openlocfilehash: ec2490bad70d2b2eb72cbb48771900f09f8c2f67
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593429"
---
# <a name="project-build-error-prj0050"></a>프로젝트 빌드 오류 PRJ0050

출력을 등록하지 못했습니다. 레지스트리를 수정 하는 적절 한 사용 권한이 확인 하세요.

Visual c + + 빌드 시스템 (dll 또는.exe) 빌드 출력을 등록할 수 없습니다. 레지스트리를 수정 하려면 관리자 권한으로 로그온 해야 합니다.

.Dll을 작성 하는 경우 regsvr32.exe를 사용 하 여 수동으로.dll을 등록 하려고 해도, 그러면 빌드 실패 원인에 대 한 정보에 표시 됩니다.

.Dll을 빌드하지 않는 경우 오류가 발생 하는 명령에 대 한 빌드 로그를 확인 합니다.