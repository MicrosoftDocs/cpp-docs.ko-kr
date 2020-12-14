---
description: '자세한 정보: 링커 도구 경고 LNK4204'
title: 링커 도구 경고 LNK4204
ms.date: 11/04/2016
f1_keywords:
- LNK4204
helpviewer_keywords:
- LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
ms.openlocfilehash: e0e61967a7b3bf42eb2c084d73c7c0aa9485c47e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294199"
---
# <a name="linker-tools-warning-lnk4204"></a>링커 도구 경고 LNK4204

' filename '에 참조 모듈에 대 한 디버깅 정보가 없습니다. 디버그 정보가 없는 것 처럼 개체를 링크 합니다.

.Pdb 파일에 잘못 된 서명이 있습니다. 링커는 디버그 정보 없이 개체를 계속 연결 합니다. [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) 옵션을 사용 하 여 개체 파일을 다시 컴파일하는 것이 좋습니다.

LNK4204 라이브러리의 일부 개체가 더 이상 존재 하지 않는 파일을 참조 하는 경우 발생할 수 있습니다. 이 문제는 솔루션을 다시 빌드하는 경우에 발생할 수 있습니다 (예:). 컴파일 오류로 인해 개체 파일이 삭제 되 고 다시 작성 되지 않을 수 있습니다. 이 경우 **/Z7** 또는 **/fd** 를 사용 하 여 컴파일하여 개체를 업데이트 하 여 라이브러리 당 단일 파일 (기본 .pdb 파일 이름 아님)을 참조 합니다.  자세한 내용은 [/fd (프로그램 데이터베이스 파일 이름)](../../build/reference/fd-program-database-file-name.md)를 참조 하세요.  소스 제어 시스템에서 업데이트 될 때마다 .pdb가 라이브러리와 함께 저장 되는지 확인 합니다.
