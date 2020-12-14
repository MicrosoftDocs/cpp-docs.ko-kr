---
description: '자세한 내용: 이전 런타임 버전에서 c + +/clr 응용 프로그램 실행'
title: 이전 버전의 런타임에서 C++ -clr 애플리케이션 실행
ms.date: 11/04/2016
helpviewer_keywords:
- applications [C++], runtime version specified
- versions [C++]
- app.config files, runtime version specified
- compatibility [C++], runtime version specified
- backward compatibility [C++], runtime version specified
- application deployment [C++], runtime version specified
- common language runtime [C++], version specified
- deploying applications [C++], runtime version specified
ms.assetid: 940171b7-6937-4b14-8e87-c199e23f4f2e
ms.openlocfilehash: 3b1bbc2906e4b347bb954c799cb9e412202a17ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247217"
---
# <a name="running-a-c-clr-application-on-a-previous-runtime-version"></a>이전 버전의 런타임에서 C++ /clr 애플리케이션 실행

별도로 지정하지 않는 한, C++ .NET Framework 애플리케이션은 컴파일러가 애플리케이션을 빌드하는 데 사용하는 CLR(공용 언어 런타임) 버전에서 실행되도록 빌드됩니다. 그러나 특정 버전의 런타임용으로 빌드된 .exe 애플리케이션은 필요한 기능을 제공하는 다른 버전에서 실행될 수 있습니다.

이 작업을 수행하려면 `supportedRuntime` 태그에 런타임 버전 정보가 포함된 app.config 파일을 제공하세요.

런타임 시 app.config 파일은 *filename.ext*.config 형식의 이름을 가져야 합니다. 여기서 *filename.ext* 는 애플리케이션을 시작한 실행 파일의 이름이고, 실행 파일과 동일한 디렉터리에 있어야 합니다. 예를 들어 애플리케이션의 이름이 TestApp.exe인 경우 app.config 파일의 이름은 TestApp.exe.config가 됩니다.

둘 이상의 런타임 버전을 지정한 상태에서 애플리케이션이 둘 이상의 런타임 버전이 설치된 컴퓨터에서 실행되는 경우, 애플리케이션은 구성 파일에 지정되어 설치된 첫 번째 버전을 사용합니다.

## <a name="see-also"></a>참고 항목

[데스크톱 애플리케이션 배포](deploying-native-desktop-applications-visual-cpp.md)
