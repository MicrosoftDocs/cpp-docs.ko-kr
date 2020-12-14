---
description: '자세한 정보: 프로젝트 빌드 오류 PRJ0034'
title: 프로젝트 빌드 오류 PRJ0034
ms.date: 11/04/2016
f1_keywords:
- PRJ0034
helpviewer_keywords:
- PRJ0034
ms.assetid: 1da4a55b-231b-4476-8545-6997628fbc00
ms.openlocfilehash: a5eb76b5a11cfed0789f6f5e5aca52e8215f4c5a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241068"
---
# <a name="project-build-error-prj0034"></a>프로젝트 빌드 오류 PRJ0034

프로젝트 수준 사용자 지정 빌드 단계의 ' 추가 종속성 ' 속성에 ' s t r u e '가 포함 되어 ' macro_expansion ' (으)로 계산 됩니다.

프로젝트에 대 한 사용자 지정 빌드 단계는 매크로 평가 문제로 인 한 추가 종속성에 오류가 포함 되어 있습니다. 이 오류는 경로 형식이 잘못 된 것을 의미할 수도 있습니다 .이 경우 파일 경로에 잘못 된 문자 또는 문자 조합이 포함 됩니다.

이 오류를 해결 하려면 매크로를 수정 하거나 경로 지정을 수정 합니다. 계산 된 경로는 프로젝트 디렉터리의 절대 경로입니다.
