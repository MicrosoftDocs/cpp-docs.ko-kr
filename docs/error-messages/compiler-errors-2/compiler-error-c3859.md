---
description: '자세한 정보: 컴파일러 오류 C3859'
title: 컴파일러 오류 C3859
ms.date: 03/08/2019
f1_keywords:
- C3859
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
ms.openlocfilehash: 25c05425072cda6924d90f08c9aeff7446a4e85b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336111"
---
# <a name="compiler-error-c3859"></a>컴파일러 오류 C3859

> PCH의 가상 메모리 범위를 초과 했습니다. '-Zm *value*' 이상의 명령줄 옵션을 사용 하 여 다시 컴파일하십시오.

미리 컴파일된 헤더에 할당 된 가상 메모리가 컴파일러에서 배치 하려는 데이터 양에 비해 너무 작습니다. Visual Studio 2015부터, **/zm** 권장 사항은 지시문을 사용 하는 경우에만 중요 합니다 `#pragma hdrstop` . 다른 경우에는 Windows 가상 메모리 압력 문제를 나타내는 의사 오류가 발생 합니다.

미리 컴파일된 헤더에서 지시문을 사용 하는 경우 `#pragma hdrstop` **/zm** 컴파일러 플래그를 사용 하 여 미리 컴파일된 헤더 파일에 대해 더 큰 값을 지정 합니다. 그렇지 않으면 빌드에서 병렬 컴파일 프로세스의 수를 줄이는 것이 좋습니다. 자세한 내용은 [/zm (미리 컴파일된 헤더 메모리 할당 제한 지정)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)을 참조 하세요.
