---
description: '자세한 정보: 심각한 오류 C1905'
title: 심각한 오류 C1905
ms.date: 11/04/2016
f1_keywords:
- C1905
helpviewer_keywords:
- C1905
ms.assetid: fefc6769-477f-45a2-9878-6f0a5f42472c
ms.openlocfilehash: 573f4b1b196bf748a2359271401c68e60a3d4b53
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276051"
---
# <a name="fatal-error-c1905"></a>심각한 오류 C1905

프런트 엔드와 백 엔드가 호환되지 않습니다. 같은 프로세서를 대상으로 해야 합니다.

이 오류는 x86, ARM 또는 x64와 같은 하나의 프로세서를 대상으로 하지만 다른 프로세서를 대상으로 하는 백 엔드 (C2.dll)에서 읽을 수 있는 컴파일러 프런트 엔드 (C1.dll)에 의해 .obj 파일이 생성 될 때 발생 합니다.

이 문제를 해결하려면 사용 중인 프런트 엔드와 백 엔드가 일치하는지 확인합니다. Visual Studio에서 만든 프로젝트의 경우 기본적으로 일치하는 프런트 엔드와 백 엔드가 사용됩니다. 컴파일러 도구에 대해 다른 경로를 사용하도록 프로젝트 파일을 편집한 경우 이 오류가 발생할 수 있습니다. 컴파일러 도구의 경로를 구체적으로 설정하지 않은 경우 설치한 Visual Studio가 손상되면 이 오류가 발생할 수 있습니다. 컴파일러 .dll 파일을 한 위치에서 다른 위치로 복사한 경우를 예로 들 수 있습니다. Windows 제어판의 **프로그램 및 기능** 을 사용 하 여 Visual Studio를 복구 하거나 다시 설치 합니다.
