---
title: DLL의 자동화
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
ms.openlocfilehash: 4ac60c44348ea21f490cb312285ae88ac682cf7d
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341660"
---
# <a name="automation-in-a-dll"></a>DLL의 자동화

MFC DLL 마법사에서 자동화 옵션을 선택하면 마법사에서 다음과 같은 항목을 제공합니다.

- 기초 개체 설명 언어 파일(.ODL)

- Afxole.h에 대한 STDAFX.h 파일의 include 지시문

- **AfxDllGetClassObject** 함수를 호출하는 `DllGetClassObject` 함수 구현

- **AfxDllCanUnloadNow** 함수를 호출하는 `DllCanUnloadNow` 함수 구현

- [COleObjectFactory::UpdateRegistryAll](../mfc/reference/coleobjectfactory-class.md#updateregistryall) 함수를 호출하는 `DllRegisterServer` 함수 구현

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [자동화 서버](../mfc/automation-servers.md)

## <a name="see-also"></a>참고자료

[Visual C++의 DLL](dlls-in-visual-cpp.md)
