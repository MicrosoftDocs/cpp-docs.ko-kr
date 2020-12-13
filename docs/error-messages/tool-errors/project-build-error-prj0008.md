---
description: '자세한 정보: 프로젝트 빌드 오류 PRJ0008'
title: 프로젝트 빌드 오류 PRJ0008
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 2ae4952dfd3e5c5f53a3f549536598402ce1fd48
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343914"
---
# <a name="project-build-error-prj0008"></a>프로젝트 빌드 오류 PRJ0008

' File ' 파일을 삭제할 수 없습니다.

**파일이 다른 프로세스에 의해 열리지 않고 쓰기 방지 되어 있지 않은지 확인 하십시오.**

다시 빌드 또는 정리 중에는 빌드에 대해 알려진 모든 중간 파일과 출력 파일을 삭제 하 고 [일반 구성 설정 속성 페이지](../../build/reference/general-property-page-project.md)에서 **정리 시 삭제할 확장** 속성의 와일드 카드 사양을 만족 하는 파일을 모두 삭제 Visual C++.

Visual C++ 파일을 삭제할 수 없는 경우이 오류가 표시 됩니다. 오류를 해결 하려면 빌드를 수행 하는 사용자를 위해 파일과 해당 디렉터리를 쓰기 가능 하도록 설정 합니다.
