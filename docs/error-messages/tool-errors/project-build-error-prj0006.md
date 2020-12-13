---
description: '자세한 정보: 프로젝트 빌드 오류 PRJ0006'
title: 프로젝트 빌드 오류 PRJ0006
ms.date: 11/04/2016
f1_keywords:
- PRJ0006
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
ms.openlocfilehash: a78646c843a6c6df3b4e2847076670492a9efb6b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343927"
---
# <a name="project-build-error-prj0006"></a>프로젝트 빌드 오류 PRJ0006

' File ' 임시 파일을 열 수 없습니다. 파일이 있으며 디렉터리가 쓰기 금지 되어 있는지 확인 하십시오.

Visual C++ 빌드 프로세스 중에 임시 파일을 만들 수 없습니다. 이러한 이유는 다음과 같습니다.

- 임시 디렉터리가 없습니다.

- 읽기 전용 임시 디렉터리입니다.

- 디스크 공간이 부족 합니다.

- $ (IntDir) 폴더는 읽기 전용 이거나 읽기 전용인 임시 파일을 포함 합니다.

PRJ0007 오류: ' directory ' 출력 디렉터리를 만들 수 없습니다. 오류가 발생 하는 경우에도이 오류가 발생 합니다. 오류 PRJ0007은 $ (IntDir) 디렉터리를 만들 수 없음을 의미 합니다. 임시 파일 만들기도 실패 합니다.

임시 파일은 다음을 지정할 때마다 생성 됩니다.

- 지시 파일입니다.

- 사용자 지정 빌드 단계입니다.

- 빌드 이벤트입니다.
