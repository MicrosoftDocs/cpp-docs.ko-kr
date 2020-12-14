---
description: '자세한 정보: 심각한 오류 C1510'
title: 심각한 오류 C1510
ms.date: 04/11/2017
f1_keywords:
- C1510
helpviewer_keywords:
- C1510
ms.assetid: 150c827f-9514-41a9-8d7e-82f820749bcb
ms.openlocfilehash: 3112874f033fdeed4cc4290b2469105a275baed8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276324"
---
# <a name="fatal-error-c1510"></a>심각한 오류 C1510

언어 리소스 clui.dll을 열 수 없습니다.

컴파일러가 언어 리소스 DLL을 로드할 수 없습니다.

이 문제에 대 한 두 가지 일반적인 원인은 다음과 같습니다. 32 비트 컴파일러 및 도구를 사용 하는 경우 링크 중에 2GB 이상의 메모리를 사용 하는 많은 프로젝트에 대해이 오류가 표시 될 수 있습니다. 64 비트 Windows 시스템에서 사용할 수 있는 솔루션은 64 비트 네이티브 또는 크로스 컴파일러와 도구를 사용 하 여 코드를 생성 하는 것입니다. 이는 64 비트 앱에 사용할 수 있는 큰 메모리 공간을 활용 합니다. 32 비트 시스템에서 실행 중 이므로 32 비트 컴파일러를 사용 해야 하는 경우에는 경우에 따라 링커에 사용할 수 있는 메모리의 양을 3GB로 늘릴 수 있습니다. 자세한 내용은 [4 기가바이트 튜닝: bcdedit 및 Boot.ini](/windows/win32/memory/4-gigabyte-tuning) 및 [bcdedit/set increaseuserva](/windows-hardware/drivers/devtest/bcdedit--set) 명령을 참조 하세요.

다른 일반적인 원인은 Visual Studio 설치가 손상 되었거나 불완전 한 경우입니다. 이 경우 설치 관리자를 다시 실행 하 여 Visual Studio를 복구 하거나 다시 설치 합니다.
