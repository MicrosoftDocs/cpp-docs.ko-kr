---
title: 리소스 전용 DLL 만들기
description: Visual Studio에서 리소스 전용 DLL을 만드는 방법
ms.date: 01/27/2020
helpviewer_keywords:
- resource-only DLLs [C++], creating
- DLLs [C++], creating
ms.assetid: e6b1d4da-7275-467f-a58c-a0a8a5835199
no-loc:
- noentry
ms.openlocfilehash: 5b7b3b4767c32bce52ad2c36c9ecc5d34b2e29b4
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922168"
---
# <a name="creating-a-resource-only-dll"></a>리소스 전용 DLL 만들기

리소스 전용 DLL은 아이콘, 비트맵, 문자열 및 대화 상자 등의 리소스만 포함된 DLL입니다. 리소스 전용 DLL을 사용하는 것은 여러 프로그램에서 동일한 리소스 집합을 공유하는 좋은 방법입니다. 여러 언어로 현지화된 리소스를 포함한 애플리케이션을 제공하는 좋은 방법이기도 합니다. 자세한 내용은 [MFC 애플리케이션에서 지역화된 리소스: 위성 DLL](localized-resources-in-mfc-applications-satellite-dlls.md)을 참조하세요.

## <a name="create-a-resource-only-dll"></a>리소스 전용 DLL 만들기

리소스 전용 DLL을 만들려면 새 Windows DLL(비 MFC) 프로젝트를 만들고 프로젝트에 리소스를 추가합니다.

::: moniker range="msvc-140"

1. **새 프로젝트** 대화 상자에서 **Win32 프로젝트** 를 선택합니다. 프로젝트 및 솔루션 이름을 입력하고 **확인** 을 선택합니다.

1. **Win32 애플리케이션 마법사** 에서 **애플리케이션 설정** 을 선택합니다. **DLL** 의 **애플리케이션 유형** 을 선택합니다. **추가 옵션** 에서 **빈 프로젝트** 를 선택합니다. **마침** 을 선택하여 프로젝트를 만듭니다.

1. DLL에 대한 리소스(예: 문자열 또는 메뉴)를 포함하는 새 리소스 스크립트를 만듭니다. `.rc` 파일을 저장합니다.

1. **프로젝트** 메뉴에서 **기존 항목 추가** 를 선택하고 프로젝트에 새 `.rc` 파일을 삽입합니다.

1. [/NOENTRY](reference/noentry-no-entry-point.md) 링커 옵션을 지정합니다. `/NOENTRY`는 링커가 `_main`에 대한 참조를 DLL에 연결할 수 없도록 합니다. 리소스 전용 DLL을 만들려면 이 옵션을 선택해야 합니다.

1. DLL을 빌드합니다.

::: moniker-end
::: moniker range=">=msvc-150"

1. **새 프로젝트** 대화 상자에서 Windows **데스크톱 마법사** 를 선택하고 **다음** 을 선택합니다. **새 프로젝트 구성** 페이지에서 프로젝트 및 솔루션 이름을 입력하고 **만들기** 를 선택합니다.

1. **Windows 데스크톱 프로젝트** 대화 상자에서 **동적 연결 라이브러리** 의 **애플리케이션 유형** 을 선택합니다. **추가 옵션** 에서 **빈 프로젝트** 를 선택합니다. **확인** 을 선택하여 프로젝트를 만듭니다.

1. DLL에 대한 리소스(예: 문자열 또는 메뉴)를 포함하는 새 리소스 스크립트를 만듭니다. `.rc` 파일을 저장합니다.

1. **프로젝트** 메뉴에서 **기존 항목 추가** 를 선택하고 프로젝트에 새 `.rc` 파일을 삽입합니다.

1. [/NOENTRY](reference/noentry-no-entry-point.md) 링커 옵션을 지정합니다. `/NOENTRY`는 링커가 `_main`에 대한 참조를 DLL에 연결할 수 없도록 합니다. 리소스 전용 DLL을 만들려면 이 옵션을 선택해야 합니다.

1. DLL을 빌드합니다.

::: moniker-end

## <a name="use-a-resource-only-dll"></a>리소스 전용 DLL 사용

리소스 전용 DLL을 사용하는 애플리케이션은 DLL에 명시적으로 연결하기 위해 [LoadLibraryEx](loadlibrary-and-afxloadlibrary.md) 또는 관련 함수를 호출해야 합니다. 리소스에 액세스하려면 `FindResource` 제네릭 함수와 모든 종류의 리소스에서 작동하는 `LoadResource`를 호출합니다. 또는 다음과 같은 리소스 특정 함수 중 하나를 호출합니다.

- `FormatMessage`

- `LoadAccelerators`

- `LoadBitmap`

- `LoadCursor`

- `LoadIcon`

- `LoadMenu`

- `LoadString`

애플리케이션은 리소스 사용을 마친 후 `FreeLibrary`를 호출해야 합니다.

## <a name="see-also"></a>참조

[리소스 파일 작업](../windows/working-with-resource-files.md)\
[Visual Studio에서 C/C++ DLL 만들기](dlls-in-visual-cpp.md)
