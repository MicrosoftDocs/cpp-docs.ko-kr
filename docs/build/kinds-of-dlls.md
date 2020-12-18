---
description: '자세한 정보: DLL 종류'
title: DLL 종류
ms.date: 05/06/2019
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
ms.openlocfilehash: 284881d9091791038c547914887275ee02605156
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156140"
---
# <a name="kinds-of-dlls"></a>DLL 종류

이 항목에서는 빌드할 DLL의 종류를 결정하는 데 도움이 되는 정보를 제공합니다.

## <a name="different-kinds-of-dlls-available"></a><a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a> 사용할 수 있는 여러 종류의 DLL

Visual Studio를 사용하면 MFC(Microsoft Foundation Class) 라이브러리를 사용하지 않는 Win32 DLL을 C 또는 C++에서 빌드할 수 있습니다. Win32 애플리케이션 마법사를 사용하여 비MFC DLL 프로젝트를 만들 수 있습니다.

MFC 라이브러리 자체는 MFC DLL 마법사로 정적 연결 라이브러리나 다수의 DLL에서 사용할 수 있습니다. DLL이 MFC를 사용 중인 경우 Visual Studio는 다음과 같은 세 가지 DLL 개발 시나리오를 지원합니다.

- 정적으로 MFC를 연결하는 기본 MFC DLL 빌드

- 동적으로 MFC를 연결하는 기본 MFC DLL 빌드

- 항상 MFC를 동적으로 연결하는 MFC 확장 DLL 빌드

### <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [비 MFC DLL: 개요](non-mfc-dlls-overview.md)

- [정적으로 MFC에 연결된 기본 MFC DLL](regular-dlls-statically-linked-to-mfc.md)

- [동적으로 MFC에 연결된 기본 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 확장명 DLL: 개요](extension-dlls-overview.md)

- [사용할 DLL의 종류](#_core_which_kind_of_dll_to_use)

## <a name="deciding-which-kind-of-dll-to-use"></a><a name="_core_which_kind_of_dll_to_use"></a> 사용할 DLL의 종류 결정

DLL에서 MFC를 사용하지 않는 경우 Visual Studio를 사용하여 비 MFC Win32 DLL을 빌드합니다. DLL을 MFC에 연결하면(정적으로 또는 동적으로) 상당한 디스크 공간과 메모리를 차지합니다. DLL이 실제로 MFC를 사용하지 않는다면 MFC에 연결해서는 안 됩니다.

DLL이 MFC를 사용하고 MFC 애플리케이션이나 비 MFC 애플리케이션에서 사용되는 경우에는 동적으로 MFC에 연결하는 기본 MFC DLL이나 정적으로 MFC에 연결하는 기본 MFC DLL을 빌드해야 합니다. DLL의 파일 크기가 훨씬 작고 MFC의 공유 버전을 사용하여 메모리를 절약하는 것이 중요할 수 있으므로 대부분의 경우는 MFC에 동적으로 연결하는 기본 MFC DLL을 사용하는 것이 좋습니다. 정적으로 MFC에 연결하는 경우 MFC 라이브러리 코드의 프라이빗 복사본을 로드하기 때문에 DLL의 파일 크기가 커지고 추가 메모리를 차지할 가능성이 있습니다.

MFC에 동적으로 연결하는 DLL을 빌드하는 것은 MFC 자체를 연결할 필요가 없으므로 정적으로 MFC에 연결하는 DLL을 빌드하는 것보다 빠릅니다. 이는 링커가 디버그 정보를 압축해야 하는 디버그 빌드에서 특히 그렇습니다. 이미 디버그 정보를 포함하는 DLL과 연결하면 DLL 내에서 압축할 디버그 정보가 줄어듭니다.

MFC에 동적으로 연결하는 것의 단점 한 가지는 공유 DLL Mfcx0.dll 및 Msvcrxx.dll(또는 유사한 파일)을 DLL과 함께 배포해야 한다는 것입니다. MFC DLL은 자유롭게 재배포할 수 있지만 그래도 여전히 설치 프로그램에 DLL을 설치해야 합니다. 또한 프로그램 및 MFC DLL 자체에서 사용되는 C 런타임 라이브러리를 포함하는 Msvcrxx.dll을 제공해야 합니다.

MFC 실행 파일에서만 DLL이 사용되는 경우에는 기본 MFC DLL 빌드와 MFC 확장 DLL 빌드 중에서 선택할 수 있습니다. DLL이 기존 MFC 클래스에서 파생된 다시 사용할 수 있는 클래스를 구현하거나 애플리케이션과 DLL 간에 MFC 파생 개체를 전달해야 하는 경우에는 MFC 확장 DLL을 빌드해야 합니다.

DLL이 동적으로 MFC에 연결하는 경우 DLL을 사용하여 MFC DLL을 재배포할 수 있습니다. 이 아키텍처는 디스크 공간을 절약하고 메모리 사용을 최소화하기 위해 여러 실행 파일 간에 클래스 라이브러리를 공유하는 데 특히 유용합니다.

### <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [비 MFC DLL: 개요](non-mfc-dlls-overview.md)

- [정적으로 MFC에 연결된 기본 MFC DLL](regular-dlls-statically-linked-to-mfc.md)

- [동적으로 MFC에 연결된 기본 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 확장명 DLL: 개요](extension-dlls-overview.md)

## <a name="see-also"></a>참조

[Visual Studio에서 C/C++ DLL 만들기](dlls-in-visual-cpp.md)
