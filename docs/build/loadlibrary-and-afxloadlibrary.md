---
title: LoadLibrary 및 AfxLoadLibrary
description: MSVC에서 Dll을 명시적으로 로드 하는 데 LoadLibrary 및 AfxLoadLibrary 사용
ms.date: 01/28/2020
f1_keywords:
- LoadLibrary
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
ms.openlocfilehash: f803212c4485f7517dc42802f1ff581ffa4e609d
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821540"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary 및 AfxLoadLibrary

는 [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) 또는 [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) 호출을 처리 하 여 DLL에 명시적으로 연결 합니다. (MFC 앱은 [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary) 또는 [AfxLoadLibraryEx](../mfc/reference/application-information-and-management.md#afxloadlibraryex)를 사용 합니다.) 함수가 성공 하면 지정 된 DLL을 호출 프로세스의 주소 공간에 매핑하고 DLL에 대 한 핸들을 반환 합니다. 핸들은 명시적 링크에 사용 되는 다른 함수 (예: `GetProcAddress` 및 `FreeLibrary`에 필요 합니다. 자세한 내용은 [명시적 링크](linking-an-executable-to-a-dll.md#linking-explicitly)를 참조 하세요.

`LoadLibrary`는 암시적 링크에 사용 되는 것과 동일한 검색 시퀀스를 사용 하 여 DLL을 찾으려고 시도 합니다. `LoadLibraryEx`를 사용 하 여 검색 경로 순서를 보다 세밀 하 게 제어할 수 있습니다. 자세한 내용은 [동적 링크 라이브러리 검색 순서](/windows/win32/dlls/dynamic-link-library-search-order)를 참조 하세요. 시스템에서 DLL을 찾을 수 없거나 진입점 함수가 FALSE를 반환 하는 경우 `LoadLibrary` NULL을 반환 합니다. `LoadLibrary`에 대 한 호출이 호출 프로세스의 주소 공간에 이미 매핑된 DLL 모듈을 지정 하는 경우 함수는 DLL의 핸들을 반환 하 고 모듈의 참조 횟수를 증가 시킵니다.

DLL에 진입점 함수가 있는 경우 운영 체제는 `LoadLibrary` 또는 `LoadLibraryEx`를 호출한 스레드의 컨텍스트에서 함수를 호출 합니다. DLL이 프로세스에 이미 연결 되어 있는 경우에는 진입점 함수가 호출 되지 않습니다. DLL에 대 한 `LoadLibrary` 또는 `LoadLibraryEx`에 대 한 이전 호출에서 `FreeLibrary` 함수를 해당 호출 하지 않은 경우에 발생 합니다.

MFC 확장 Dll을 로드 하는 MFC 응용 프로그램의 경우에는 `LoadLibrary` 또는 `LoadLibraryEx`대신 `AfxLoadLibrary` 또는 `AfxLoadLibraryEx`를 사용 하는 것이 좋습니다. MFC 함수는 DLL을 명시적으로 로드 하기 전에 스레드 동기화를 처리 합니다. `AfxLoadLibrary` 및 `AfxLoadLibraryEx`에 대 한 인터페이스 (함수 프로토타입)는 `LoadLibrary` 및 `LoadLibraryEx`와 동일 합니다.

Windows에서 DLL을 로드할 수 없는 경우 프로세스에서 오류 복구를 시도할 수 있습니다. 예를 들어 사용자에 게 오류를 알린 다음 DLL에 대 한 다른 경로를 요청할 수 있습니다.

> [!IMPORTANT]
> 모든 Dll의 전체 경로를 지정 해야 합니다. `LoadLibrary`에서 파일을 로드할 때 먼저 현재 디렉터리를 검색할 수 있습니다. 파일의 경로를 정규화 하지 않으면 의도 한 파일이 아닌 파일이 로드 될 수 있습니다. DLL을 만들 때 [/DEPENDENTLOADFLAG](reference/dependentloadflag.md) 링커 옵션을 사용 하 여 정적으로 연결 된 dll 종속성의 검색 순서를 지정할 수 있습니다. Dll 내에서 전체 경로를 사용 하 여 종속성을 명시적으로 로드 하 고 `LoadLibraryEx` 또는 `AfxLoadLibraryEx` 호출 매개 변수를 사용 하 여 모듈 검색 순서를 지정 합니다. 자세한 내용은 [동적 연결 라이브러리 보안](/windows/win32/dlls/dynamic-link-library-security) 및 [동적 링크 라이브러리 검색 순서](/windows/win32/dlls/dynamic-link-library-search-order)를 참조 하세요.

## <a name="what-do-you-want-to-do"></a>원하는 옵션을 선택하세요.

- [DLL에 실행 파일 링크](linking-an-executable-to-a-dll.md#linking-implicitly)

- [DLL에 실행 파일 링크](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [동적 연결 라이브러리 검색 순서](/windows/win32/Dlls/dynamic-link-library-search-order)

- [FreeLibrary 및 AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>참조

- [Visual Studio에서 C/C++ DLL 만들기](dlls-in-visual-cpp.md)
