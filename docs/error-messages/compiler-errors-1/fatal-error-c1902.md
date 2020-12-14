---
description: '자세한 정보: 심각한 오류 C1902'
title: 심각한 오류 C1902
ms.date: 11/04/2016
f1_keywords:
- C1902
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
ms.openlocfilehash: e41f1d6fa9e15f9ed748b6e916ef8d8dd314b3f6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276090"
---
# <a name="fatal-error-c1902"></a>심각한 오류 C1902

프로그램 데이터베이스 관리자가 일치 하지 않습니다. 설치를 확인 하세요.

컴파일러가 시스템에서 찾은 것 보다 최신 버전의 mspdb *XXX*.dll을 사용 하 여 프로그램 데이터베이스 파일 (.pdb)을 만들었습니다. 이 오류는 일반적으로 mspdbsrv.exe 또는 mspdbcore.dll *없거나 mspdb와* 다른 버전이 있음을 나타냅니다. Mspdb *xxx*.dll 파일 이름의 *xxx* 자리 표시자는 각 제품 릴리스와 함께 변경 됩니다. 예를 들어 Visual Studio 2015에서는 파일 이름이 mspdb140.dll입니다.

mspdbsrv.exe, mspdbcore.dll *및 mspdb의* 일치 하는 버전이 시스템에 설치 되어 있는지 확인 합니다. 일치 하지 않는 버전이 대상 플랫폼에 대 한 컴파일러 및 링크 도구를 포함 하는 디렉터리에 복사 되지 않았는지 확인 합니다. 예를 들어 **PATH** 환경 변수를 적절 하 게 설정 하지 않고 명령 프롬프트에서 컴파일러 또는 링크 도구를 호출할 수 있도록 파일을 복사 했을 수 있습니다.
