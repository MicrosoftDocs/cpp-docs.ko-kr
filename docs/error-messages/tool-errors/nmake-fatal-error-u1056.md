---
description: '자세한 정보: NMAKE 심각한 오류 U1056'
title: NMAKE 심각한 오류 U1056
ms.date: 11/04/2016
f1_keywords:
- U1056
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
ms.openlocfilehash: beb7814d2e29665e1f92c7ef1e8dadbd66af5d63
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330380"
---
# <a name="nmake-fatal-error-u1056"></a>NMAKE 심각한 오류 U1056

명령 처리기를 찾을 수 없습니다.

명령 프로세서가 **COMSPEC** 또는 **path** 환경 변수에 지정 된 경로에 없습니다.

NMAKE는 명령을 실행할 때 COMMAND.COM 또는 CMD.EXE를 명령 프로세서로 사용 합니다. **COMSPEC** 에 설정 된 경로에서 먼저 명령 처리기를 찾습니다. **COMSPEC** 가 없는 경우 NMAKE는 **PATH** 에 지정 된 디렉터리를 검색 합니다.
