---
description: '자세한 정보: pgomgr'
title: pgomgr
ms.date: 03/14/2018
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
ms.openlocfilehash: 3b6b969becde43b98ea06f2058dd235eaf0acbed
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187353"
---
# <a name="pgomgr"></a>pgomgr

하나 이상의 .pgc 파일에 있는 프로필 데이터를 .pgd 파일에 추가합니다.

## <a name="syntax"></a>구문

> **pgomgr** [*options*] *pgcfiles* *pgdfile*

### <a name="parameters"></a>매개 변수

*options*<br/>
**pgomgr** 에 지정할 수 있는 옵션은 다음과 같습니다.

- **/help** 또는 **/?** 사용 가능한 **pgomgr** 옵션을 표시합니다.

- **/clear** .pgd 파일의 모든 프로필 정보를 지웁니다. **/clear** 를 지정하면 .pgc 파일을 지정할 수 없습니다.

- **/detail** 흐름 그래프 적용 범위 정보를 포함하여 자세한 통계를 표시합니다.

- **/summary** 함수별 통계를 표시합니다.

- **/unique** **/summary** 와 함께 사용하면 데코레이트된 함수 이름이 표시됩니다. 기본값은 **/unique** 를 사용하지 않는 경우 데코레이트되지 않은 함수 이름이 표시되는 것입니다.

- **/merge**\[ **:** <em>n</em>] .pgc 파일의 데이터를 .pgd 파일에 추가합니다. 선택적 매개 변수 *n* 을 사용하면 데이터를 *n* 번 추가하도록 지정할 수 있습니다. 예를 들어 고객이 수행하는 빈도를 반영해 시나리오가 일반적으로 6번 수행되는 경우 시나리오를 테스트 실행에서 한 번 수행하고 **pgomgr /merge:6** 을 사용하여 .pgd 파일에 6번 추가할 수 있습니다.

*pgcfiles*<br/>
.pgd 파일에 병합하려는 프로필 데이터가 포함된 하나 이상의 .pgc 파일입니다. 단일 .pgc 파일이나 여러 .pgc 파일을 지정할 수 있습니다. .pgc 파일을 지정하지 않으면 **pgomgr** 은 파일 이름이 .pgd 파일과 동일한 모든 .pgc 파일을 병합합니다.

*pgdfile*<br/>
.pgc 파일의 데이터를 병합하는 .pgd 파일입니다.

## <a name="remarks"></a>설명

> [!NOTE]
> 이 도구는 Visual Studio 개발자 명령 프롬프트에서만 시작할 수 있습니다. 시스템 명령 프롬프트 또는 파일 탐색기에서는 시작할 수 없습니다.

## <a name="example"></a>예제

이 예제 명령은 myapp.pgd 파일에서 프로필 데이터를 지웁니다.

`pgomgr /clear myapp.pgd`

이 예제 명령은 myapp1.pgc의 프로필 데이터를 .pgd 파일에 세 번 추가합니다.

`pgomgr /merge:3 myapp1.pgc myapp.pgd`

이 예제에서는 모든 myapp#.pgc 파일의 프로필 데이터를 myapp.pgd 파일에 추가합니다.

`pgomgr -merge myapp1.pgd`

## <a name="see-also"></a>참조

[프로필 기반 최적화](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
[pgosweep](pgosweep.md)<br/>
