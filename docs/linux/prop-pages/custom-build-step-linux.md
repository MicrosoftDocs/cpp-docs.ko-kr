---
description: '자세한 정보: 사용자 지정 빌드 단계 속성(Linux C++)'
title: 사용자 지정 빌드 단계 속성(Linux C++)
ms.date: 06/07/2019
ms.assetid: 77a9c1fb-7c41-4a9b-9418-18ac17ce4e74
ms.openlocfilehash: d8a120d147d107cd96f77556a412aa8ee6636548
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169777"
---
# <a name="custom-build-step-properties-linux-c"></a>사용자 지정 빌드 단계 속성(Linux C++)

::: moniker range="msvc-140"

Linux 지원은 Visual Studio 2017 이상에서 사용할 수 있습니다.

::: moniker-end

::: moniker range=">=msvc-150"

| 속성 | Description |
|--|--|
| 명령줄 | 사용자 지정 빌드 단계에서 실행할 명령입니다. |
| Description | 사용자 지정 빌드 단계를 실행할 때 표시되는 메시지입니다. |
| outputs | 사용자 지정 빌드 단계에서 생성되는 출력 파일입니다. 증분 빌드가 올바로 작동하려면 이 설정이 필요합니다. |
| 추가 종속성 | 사용자 지정 빌드 단계에 사용할 추가 입력 파일의 세미콜론으로 구분한 목록입니다. |
| 이후 실행 및 이전 실행 | 이러한 옵션은 나열된 대상 기준으로 빌드 프로세스에서 사용자 지정 빌드 단계가 실행되는 때를 정의합니다. 가장 일반적으로 나열되는 대상은 빌드 프로세스의 주요 단계를 나타내는 BuildGenerateSources, BuildCompile, BuildLink입니다. 종종 나열되는 다른 대상은 Midl, CLCompile, Link입니다. |
| 출력을 콘텐츠로 처리 | 이 옵션은 .appx 패키지의 모든 콘텐츠 파일을 포함하는 Microsoft Store 또는 Windows Phone 앱에만 의미가 있습니다. |

::: moniker-end
