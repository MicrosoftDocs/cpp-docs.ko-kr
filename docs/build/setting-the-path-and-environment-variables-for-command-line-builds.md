---
description: '자세한 정보: 명령줄 빌드에 맞는 경로 및 환경 변수 설정'
title: 명령줄 빌드에 맞는 경로 및 환경 변수 설정
ms.custom: conceptual
ms.date: 07/24/2019
helpviewer_keywords:
- environment variables [C++]
- VCVARS32.bat file
- cl.exe compiler [C++], environment variables
- LINK tool [C++], environment variables
- PATH reserved word
- INCLUDE reserved word
- LINK tool [C++], path
- LIB environment variable
- compiling source code [C++], from command line
- environment variables [C++], CL compiler
ms.assetid: 99389528-deb5-43b9-b99a-03c8773ebaf4
ms.openlocfilehash: 3accc1cf56b86822298e1f1298bcae7d41c28332
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275388"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>명령줄 빌드에 맞는 경로 및 환경 변수 설정

Microsoft C++(MSVC) 명령줄 빌드 도구에는 설치 및 빌드 구성에 맞게 사용자 지정된 여러 환경 변수가 필요합니다. Visual Studio 설치 관리자가 C++ 워크로드를 설치할 때 필요한 환경 변수를 설정하는 사용자 지정 명령 파일 또는 배치 파일을 만듭니다. 그런 다음 설치 관리자는 이러한 명령 파일을 사용하여 개발자 명령 프롬프트 창을 여는 Windows 시작 메뉴의 바로 가기를 만듭니다. 이러한 바로 가기는 특정 빌드 구성에 대한 환경 변수를 설정합니다. 명령줄 도구를 사용하려면 다음 바로 가기 중 하나를 실행하거나, 일반 명령 프롬프트 창을 연 다음 사용자 지정 명령 파일 중 하나를 실행하여 빌드 구성 환경을 직접 설정할 수 있습니다. 자세한 내용은 [명령줄에서 MSVC 도구 집합 사용](building-on-the-command-line.md)을 참조하세요. 일반 명령 프롬프트에서 명령 파일을 사용하려면 [개발자 명령 파일 위치](building-on-the-command-line.md#developer_command_file_locations) 섹션을 참조하세요.

MSVC 명령줄 도구는 PATH, TMP, INCLUDE, LIB 및 LIBPATH 환경 변수를 사용하고, 설치된 도구, 플랫폼 및 SDK와 관련된 다른 환경 변수를 사용합니다. 간단한 Visual Studio 설치에서도 20개 이상의 환경 변수를 설정할 수 있습니다. 이러한 환경 변수 값은 설치 및 빌드 구성에 따라 달라지며 제품 업데이트 또는 업그레이드를 통해 변경할 수 있으므로 Windows 환경에서 직접 설정하는 대신 개발자 명령 프롬프트 바로 가기 또는 사용자 지정 명령 파일 중 하나를 사용하여 설정하는 것이 가장 좋습니다.

개발자 명령 프롬프트 바로 가기에서 설정된 환경 변수를 확인하려면 SET 명령을 사용할 수 있습니다. 일반 명령 프롬프트 창을 열고 기준을 위한 SET 명령의 출력을 캡처합니다. 개발자 명령 프롬프트 창을 열고 비교를 위한 SET 명령의 출력을 캡처합니다. Visual Studio IDE에 기본 제공되는 것과 같은 diff 도구는 환경 변수를 비교하여 개발자 명령 프롬프트에서 설정된 항목을 확인하는 데 유용할 수 있습니다. 컴파일러 및 링커에서 사용하는 특정 환경 변수에 대한 자세한 내용은 [CL 환경 변수](reference/cl-environment-variables.md)를 참조하세요.

> [!NOTE]
> 많은 명령줄 도구 또는 도구 옵션은 사용하려면 관리자 권한이 필요할 수 있습니다. 사용 권한 문제가 있는 경우 **관리자 권한으로 실행** 옵션을 사용하여 개발자 명령 프롬프트 창을 여는 것이 좋습니다. Windows 10에서 마우스 오른쪽 단추를 클릭하여 명령 프롬프트 창의 바로 가기 메뉴를 연 다음 **추가**, **관리자 권한으로 실행** 을 선택합니다.

## <a name="see-also"></a>참조

[명령줄에서 MSVC 도구 집합 사용](building-on-the-command-line.md)<br/>
[MSVC 링커 참조](reference/linking.md)<br/>
[MSVC 링커 옵션](reference/linker-options.md)<br/>
[MSVC 컴파일러 참조](reference/compiling-a-c-cpp-program.md)<br/>
[MSVC 컴파일러 옵션](reference/compiler-options.md)
