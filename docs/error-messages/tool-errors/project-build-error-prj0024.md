---
description: '자세한 정보: 프로젝트 빌드 오류 PRJ0024'
title: 프로젝트 빌드 오류 PRJ0024
ms.date: 08/27/2018
f1_keywords:
- PRJ0024
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
ms.openlocfilehash: e42df62181d02cf8d4696cc4f48afcec52cd4d76
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150464"
---
# <a name="project-build-error-prj0024"></a>프로젝트 빌드 오류 PRJ0024

> '*Path*' 유니코드 경로를 사용자의 ANSI 코드 페이지로 변환할 수 없습니다.

*path* 는 원래 유니코드 버전의 경로 문자열입니다. 이 오류는 현재 시스템 코드 페이지에 대해 ANSI로 직접 변환할 수 없는 유니코드 경로가 있는 경우에 발생할 수 있습니다.

이 오류는 컴퓨터에 없는 코드 페이지를 사용 하 여 시스템에서 개발한 프로젝트로 작업 하는 경우 발생할 수 있습니다.

이 오류에 대 한 해결 방법은 ANSI 텍스트를 사용 하는 경로를 업데이트 하거나 컴퓨터에 코드 페이지를 설치 하 고 시스템 기본값으로 설정 하는 것입니다.
