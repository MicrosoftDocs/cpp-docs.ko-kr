---
description: '자세한 정보: 링커 도구 오류 LNK1318'
title: 링커 도구 오류 LNK1318
ms.date: 05/29/2018
f1_keywords:
- LNK1318
helpviewer_keywords:
- LNK1318
ms.openlocfilehash: c92a88f7c26e750ff7d5aace1683827c4d61da1e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310694"
---
# <a name="linker-tools-error-lnk1318"></a>링커 도구 오류 LNK1318

> 예기치 않은 PDB 오류입니다. *원인* '*세부 정보*'

링커에서 PDB 파일을 열거나 읽고 쓸 때 예기치 않은 오류가 발생 했습니다.

이 오류 메시지는 PDB 파일에서 흔히 발생 하는 문제에 대해 생성 됩니다. *원인과* *세부 정보* 는 오류가 발생 했을 때 링커에 사용할 수 있는 정보를 나타냅니다. 이는 PDB 파일을 처리할 때 일반적인 오류로 인해 별도의 추가 정보 오류 메시지가 있는 경우에는 매우 유용 하지 않을 수 있습니다.

오류의 소스가 일반적이 지 않기 때문에이 문제를 해결 하는 데 사용할 수 있는 일반 조언이 있습니다.

- 빌드 디렉터리에서 정리 작업을 수행 하 고 솔루션의 전체 빌드를 수행 합니다.

- 컴퓨터를 다시 부팅 하거나, TaskManager에서 중단 되거나 응답 하지 않는 mspdbsrv.exe 프로세스를 확인 하 고 종료 합니다.

- 프로젝트 디렉터리에서 바이러스 검사를 해제 합니다.

- MSBuild 또는 다른 병렬 빌드 프로세스에서 [/mp](../../build/reference/mp-build-with-multiple-processes.md) 를 사용 하는 경우 [/zf](../../build/reference/zf.md) 컴파일러 옵션을 사용 합니다.

- 64 비트 호스트 된 도구 집합을 사용 하 여 빌드를 시도 합니다.

- 필요한 경우 병렬 링크 문제를 완화 하기 위해 링크를 직렬화 합니다. 이 오류는 한 링크 인스턴스에서 mspdbsrv.exe를 시작 하 여 다른 링크 인스턴스를 사용 하 여 작업을 수행 하기 전에 종료 되는 경우에 발생할 수 있습니다. 이 수정의 단점은 프로젝트 빌드를 완료 하는 데 시간이 상당히 오래 걸릴 수 있다는 것입니다.
