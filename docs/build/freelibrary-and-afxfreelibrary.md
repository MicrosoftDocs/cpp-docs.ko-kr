---
description: '자세한 정보: FreeLibrary 및 AfxFreeLibrary'
title: FreeLibrary 및 AfxFreeLibrary
ms.date: 11/04/2016
f1_keywords:
- FreeLibrary
- AfxFreeLibrary
helpviewer_keywords:
- extension DLLs [C++], unloading
- AfxFreeLibrary method
- unloading DLLs
- FreeLibrary method
- DLLs [C++], linking
- explicit linking [C++]
- DLLs [C++], unloading
ms.assetid: 4a48d290-3971-43e9-8e97-ba656cd0c8f8
ms.openlocfilehash: ea4da8c69aa663add85e740d99b68731e263b442
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162796"
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary 및 AfxFreeLibrary

DLL 모듈이 더 이상 필요하지 않은 경우 DLL에 명시적으로 연결하는 프로세스는 [FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary) 함수를 호출합니다. 이 함수는 모듈의 참조 횟수를 감소시킵니다. 참조 횟수가 0인 경우 프로세스의 주소 공간에서 매핑되지 않습니다.

MFC 애플리케이션에서 `FreeLibrary` 대신 [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)를 사용하여 MFC 확장명 DLL을 언로드합니다. `AfxFreeLibrary`에 대한 인터페이스(함수 프로토타입)는 `FreeLibrary`와 동일합니다.

## <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [DLL에 실행 파일 링크](linking-an-executable-to-a-dll.md#linking-implicitly)

- [DLL에 실행 파일 링크](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [LoadLibrary 및 AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>참조

[Visual Studio에서 C/C++ DLL 만들기](dlls-in-visual-cpp.md)\
[FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)\
[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)
