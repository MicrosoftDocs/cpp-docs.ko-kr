---
description: '자세한 정보: CLR 프로젝트용으로 만든 파일'
title: CLR 프로젝트용 파일
ms.date: 11/04/2016
helpviewer_keywords:
- Visual Studio C++ projects, CLR programming
- .NET applications, C++
ms.assetid: 59ae9020-5f26-4ad0-bbdd-97c2e2023a20
ms.openlocfilehash: 14aa07d891a75307f119f33ace5c32dbb2aa18db
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200528"
---
# <a name="files-created-for-clr-projects"></a>CLR 프로젝트용 파일

Visual C++ 템플릿을 사용하여 프로젝트를 만들 때 사용하는 템플릿에 따라 여러 개의 파일이 생성됩니다. 다음 표에서는 .NET Framework 프로젝트의 프로젝트 템플릿에서 만든 모든 파일을 나열합니다.

|파일 이름|파일 설명|
|---------------|----------------------|
|AssemblyInfo.cpp|프로젝트의 어셈블리 메타데이터를 수정하기 위한 정보(즉, 특성, 파일, 리소스, 형식, 버전 정보, 서명 정보 등)를 포함하는 파일입니다. 자세한 내용은 [어셈블리 개념](/dotnet/framework/app-domains/assembly-contents)을 참조하세요.|
|*projname*.asmx|XML Web services의 기능을 캡슐화하는 관리 클래스를 참조하는 텍스트 파일입니다.|
|*projname*.cpp|Visual Studio에서 만든 주 원본 파일 및 애플리케이션에 대한 진입점입니다. 프로젝트 .dll 파일 및 프로젝트 네임스페이스를 식별합니다. 이 파일에 사용자 고유의 코드를 제공합니다.|
|*projname*.vsdisco|XML Web services를 설명하는 다른 리소스에 대한 링크를 포함하는 XML 배포 파일입니다.|
|*projname*.h|모든 선언, 전역 기호 및 다른 헤더 파일의 `#include` 지시문을 포함하는 프로젝트의 주 포함 파일입니다.|
|*projname*.sln|프로젝트의 모든 요소를 단일 솔루션으로 구성하기 위해 개발 환경 내에서 사용되는 솔루션 파일입니다.|
|*projname*.suo|개발 환경 내에서 사용되는 솔루션 옵션 파일입니다.|
|*projname*.vcxproj|이 프로젝트에 특정된 정보를 저장하는 개발 환경 내에서 사용되는 프로젝트 파일입니다.|
|ReadMe.txt|템플릿에서 만든 실제 파일 이름을 사용하여 프로젝트의 각 파일을 설명하는 파일입니다.|
