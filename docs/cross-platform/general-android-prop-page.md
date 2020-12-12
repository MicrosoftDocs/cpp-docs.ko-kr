---
description: '자세히 알아보기: 일반 프로젝트 속성 (Android c + +)'
title: 일반 프로젝트 속성(Android C++)
ms.date: 10/23/2017
ms.assetid: 65f4868b-b864-4989-a275-1e51869ef599
f1_keywords:
- VC.Project.VCConfiguration.Android.OutputDirectory
- VC.Project.VCConfiguration.Android.IntermediateDirectory
- VC.Project.VCConfiguration.Android.TargetName
- VC.Project.VCConfiguration.Android.TargetExt
- VC.Project.VCConfiguration.Android.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.Android.BuildLogFile
- VC.Project.VCConfiguration.Android.PlatformToolset
- VC.Project.VCConfiguration.Android.ConfigurationType
- VC.Project.VCConfiguration.UseOfSTL
- VC.Project.VCConfiguration.ThumbMode
ms.openlocfilehash: 84f45afad9cc36eb0fbe5b2dd1da895b3e50fcea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319237"
---
# <a name="general-project-properties-android-c"></a>일반 프로젝트 속성(Android C++)

| 속성 | 설명 | 선택 항목 |
|--|--|--|
| 출력 디렉터리 | 출력 파일 디렉터리에 대한 상대 경로를 지정하며 환경 변수를 포함할 수 있습니다. |
| 중간 디렉터리 | 중간 파일 디렉터리에 대한 상대 경로를 지정하며 환경 변수를 포함할 수 있습니다. |
| 대상 이름 | 이 프로젝트가 생성 하는 파일 이름을 지정 합니다. |
| 대상 확장명 | 이 프로젝트가 생성 하는 파일 확장명을 지정 합니다. (예제: *.exe* 또는 *.dll*) |
| 정리할 때 삭제할 확장명 | 정리하거나 다시 빌드할 때 삭제할 중간 디렉터리에 있는 파일에 대한 세미콜론으로 구분된 와일드카드 규칙입니다. |
| 빌드 로그 파일 | 빌드 로깅을 사용하도록 설정된 경우 작성할 빌드 로그 파일을 지정합니다. |
| 플랫폼 도구 집합 | 현재 구성을 빌드하는 데 사용하는 도구 집합을 지정합니다. 지정하지 않으면 기본 도구 집합이 사용됩니다. |
| 구성 유형 | 이 구성에서 생성하는 출력 형식을 지정합니다. | **동적 라이브러리 (.)** -동적 라이브러리 (*.*)<br>**정적 라이브러리 (. a)** -정적 라이브러리 (*. a*)<br>**유틸리티** - 유틸리티<br>**메이크파일** - 메이크파일<br> |
| 대상 API 수준 | 이 구성에서 대상으로 지정된 Android NDK API 수준입니다. |
| STL 사용 | 이 구성에 대해 사용할 C++ 표준 라이브러리를 지정합니다. | **최소 C++ 런타임 라이브러리(시스템)**<br>**C++ 런타임 정적 라이브러리(gabi++_static)**<br>**C++ 런타임 공유 라이브러리(gabi++_shared)**<br>**STLport 런타임 정적 라이브러리(stlport_static)**<br>**STLport 런타임 공유 라이브러리(stlport_shared)**<br>**GNU STL 정적 라이브러리(gnustl_static)**<br>**GNU STL 공유 라이브러리(gnustl_shared)**<br>**LLVM libc++ 정적 라이브러리(c++_static)**<br>**LLVM libc++ 공유 라이브러리(c++_shared)**<br> |
| Thumb 모드 | Thumb 마이크로 아키텍처용으로 실행되는 코드를 생성합니다. 이는 arm 아키텍처에만 적용됩니다. | **손잡이**<br>**암**<br>**사용 안 함**<br> |
