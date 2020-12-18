---
description: '자세한 정보: 방법: 여러 개의 PGO 프로필을 단일 프로필로 병합'
title: '방법: 여러 개의 PGO 프로필을 단일 프로필로 병합'
ms.date: 03/14/2018
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
ms.openlocfilehash: 9549b9a26b0c16300c3750159f2c18c74dd293b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162692"
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>방법: 여러 개의 PGO 프로필을 단일 프로필로 병합

PGO(프로필 기반 최적화)는 프로파일링된 시나리오를 기반으로 최적화된 이진 파일을 만드는 데 유용한 도구입니다. 하지만 중요하지만 고유한 여러 시나리오를 포함하는 애플리케이션이 있으면 어떻게 해야 하나요? PGO가 여러 가지 시나리오에서 사용할 수 있는 단일 프로필을 만들려면 어떻게 하나요? Visual Studio에서는 PGO Manager [pgomgr.exe](pgomgr.md)가 이 작업을 수행합니다.

프로필을 병합하는 구문은 다음과 같습니다.

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

여기서 `num`은 이 병합으로 추가된 .pgc 파일에 사용할 선택적 가중치입니다. 가중치는 일부 시나리오가 다른 시나리오보다 중요하거나 여러 번 실행해야 하는 시나리오가 있는 경우 일반적으로 사용됩니다.

> [!NOTE]
> 오래된 프로필 데이터를 사용하는 경우 PGO Manager가 작동하지 않습니다. .pgc 파일을 .pgd 파일에 병합하려면 .pgd 파일을 생성한 동일한 링크 호출로 생성된 실행 파일로 .pgc 파일을 생성해야 합니다.

## <a name="examples"></a>예

이 예제에서는 PGO Manager가 pgcFile.pgc를 pgdFile.pgd에 6번 추가합니다.

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

이 예제에서는 PGO Manager가 pgcFile1.pgc 및 pgcFile2.pgc를 각 .pgc 파일에 대해 두 번씩 pgdFile.pgd에 추가합니다.

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

PGO Manager를 .pgc 파일 인수 없이 실행하면 PGO Manager는 로컬 디렉터리에서 .pgd 파일 이름 다음에 느낌표(!)와 하나 이상의 임의의 문자가 오는 이름과 같은 기본 이름을 가진 모든 .pgc 파일을 검색합니다. 예를 들어 로컬 디렉터리에 test.pgd, test!1.pgc, test2.pgc 및 test!hello.pgc 파일이 있는 경우 다음 명령이 로컬 디렉터리에서 실행된 후 **pgomgr** 가 test!1.pgc 및 test!hello.pgc를 test.pgd에 병합합니다.

`pgomgr /merge test.pgd`

## <a name="see-also"></a>참조

[프로필 기반 최적화](profile-guided-optimizations.md)
