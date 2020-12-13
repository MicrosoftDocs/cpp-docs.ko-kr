---
description: '자세한 정보: 강력한 이름 어셈블리 (어셈블리 서명) (c + +/CLI)'
title: 강력한 이름 어셈블리(어셈블리 서명)(C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- assemblies [C++]
- signing assemblies
- .NET Framework [C++], assembly signing
- assemblies [C++], signing
- linker [C++], assembly signing
- strong-named assemblies [C++]
ms.assetid: c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc
ms.openlocfilehash: 9fc08df759fa384ed13dbe3d8c3eb2d843183517
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335313"
---
# <a name="strong-name-assemblies-assembly-signing-ccli"></a>강력한 이름 어셈블리(어셈블리 서명)(C++/CLI)

이 항목에서는 어셈블리에 서명 하는 방법에 대해 설명 합니다. 일반적으로 어셈블리에 강력한 이름을 지정 하는 것이 라고도 합니다.

## <a name="remarks"></a>설명

Visual C++ 사용 하는 경우 어셈블리 서명에 대 한 CLR 특성과 관련 된 문제를 방지 하기 위해 링커 옵션을 사용 하 여 어셈블리에 서명 합니다.

- <xref:System.Reflection.AssemblyDelaySignAttribute>

- <xref:System.Reflection.AssemblyKeyFileAttribute>

- <xref:System.Reflection.AssemblyKeyNameAttribute>

특성을 사용 하지 않는 이유는 키 이름이 어셈블리 메타 데이터에 표시 되는 것입니다 .이 경우 파일 이름에 기밀 정보가 포함 되어 있으면 보안상 위험할 수 있습니다. 또한 Visual C++ 개발 환경에서 사용 하는 빌드 프로세스는 CLR 특성을 사용 하 여 어셈블리에 강력한 이름을 지정한 다음 어셈블리에 대 한 mt.exe와 같이 사후 처리 도구를 실행 하는 경우 어셈블리가 서명 되는 키를 무효화 합니다.

명령줄에서 빌드하는 경우 링커 옵션을 사용 하 여 어셈블리에 서명한 다음 사후 처리 도구 (예: mt.exe)를 실행 합니다. 그러면 sn.exe를 사용 하 여 어셈블리에 다시 서명 해야 합니다. 또는 어셈블리 서명을 빌드하고 지연 하 고 사후 처리 도구를 실행 한 후 서명을 완료할 수 있습니다.

개발 환경에서 빌드할 때 서명 특성을 사용 하는 경우 빌드 후 이벤트에서 sn.exe ([Sn.exe (강력한 이름 도구)](/dotnet/framework/tools/sn-exe-strong-name-tool))을 명시적으로 호출 하 여 어셈블리에 성공적으로 서명할 수 있습니다. 자세한 내용은 [빌드 이벤트 지정](../build/specifying-build-events.md)을 참조하세요. 특성과 빌드 후 이벤트를 사용 하는 경우 링커 옵션을 사용 하는 것과 비교 하 여 빌드 시간을 줄일 수 있습니다.

다음 링커 옵션은 어셈블리 서명을 지원 합니다.

- [/DELAYSIGN (어셈블리에 부분적으로 서명)](../build/reference/delaysign-partially-sign-an-assembly.md)

- [/KEYFILE (어셈블리에 서명할 키 또는 키 쌍 지정)](../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER (어셈블리에 서명할 키 컨테이너 지정)](../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

강력한 어셈블리에 대 한 자세한 내용은 [Strong-Named 어셈블리 만들기 및 사용](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[C + +/CLI를 사용한 .NET 프로그래밍 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
