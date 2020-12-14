---
description: '자세한 정보: 링커 도구 오류 LNK2023'
title: 링커 도구 오류 LNK2023
ms.date: 11/04/2016
f1_keywords:
- LNK2023
helpviewer_keywords:
- LNK2023
ms.assetid: c99e35a8-739a-4a20-a715-29b8c3744703
ms.openlocfilehash: fbcddcb00d77fd1b51effb27bc032019fc803d3c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275817"
---
# <a name="linker-tools-error-lnk2023"></a>링커 도구 오류 LNK2023

dll 또는 진입점이 잘못 되었습니다. \<dll or entry point>

링커가 잘못 된 버전의 msobj90.dll를 로드 하 고 있습니다. 경로의 link.exe와 msobj90.dll의 버전이 같은지 확인 합니다.

msobj90.dll 종속성이 없을 수 있습니다. msobj90.dll에 대 한 종속성 목록은 다음과 같습니다.

- Msvcr90.dll

- Kernel32.dll

컴퓨터에 최신 상태가 아닐 수 있는 msobj90.dll의 다른 복사본이 있는지 확인 합니다.
