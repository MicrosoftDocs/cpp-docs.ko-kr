---
description: '자세한 정보: MFC 확장 DLL: 개요'
title: '확장 DLL: 개요'
ms.date: 05/06/2019
helpviewer_keywords:
- AFXDLL library
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: eb5e10b7-d615-4bc7-908d-e3e99b7b1d5f
ms.openlocfilehash: b877eeaae2e67466d4b695820659c5718d552d0e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162926"
---
# <a name="mfc-extension-dlls-overview"></a>MFC 확장 DLL: 개요

MFC 확장 DLL은 일반적으로 기존 MFC 라이브러리 클래스에서 파생된 다시 사용할 수 있는 클래스를 구현하는 DLL입니다. MFC 확장 DLL은 MFC의 동적 연결 라이브러리 버전(MFC의 공유 버전이라고도 함)을 사용하여 빌드됩니다. 공유 버전의 MFC로 빌드된 MFC 실행 파일(애플리케이션 또는 기본 MFC DLL)만 MFC 확장 DLL을 사용할 수 있습니다. MFC 확장 DLL을 사용하면 MFC에서 새로운 사용자 지정 클래스를 파생한 다음 이 확장 버전의 MFC를 DLL을 호출하는 애플리케이션에 제공할 수 있습니다.

MFC에서 파생된 개체를 애플리케이션과 DLL 간에 전달하는 데에도 확장 DLL을 사용할 수 있습니다. 전달된 개체와 연결된 멤버 함수는 개체가 생성된 모듈에 있습니다. MFC의 공유 DLL 버전을 사용할 때 관련 함수를 제대로 내보내므로 MFC 또는 MFC 파생 개체 포인터는 애플리케이션과 애플리케이션에서 로드하는 MFC 확장 DLL 간에 자유롭게 전달할 수 있습니다.

MFC 확장 DLL의 기본 요구 사항을 충족하는 DLL의 예제는 MFC 샘플 [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)를 참조하세요. 특히 Testdll1.cpp 및 Testdll2.cpp 파일을 살펴보세요.

## <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [MFC 확장 DLL 초기화](run-time-library-behavior.md#initializing-extension-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [MFC 확장명 DLL](extension-dlls.md)

- [기본 MFC DLL에서 데이터베이스, OLE 및 소켓 MFC 확장명 DLL 사용](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [비 MFC DLL: 개요](non-mfc-dlls-overview.md)

- [정적으로 MFC에 연결된 기본 MFC DLL](regular-dlls-statically-linked-to-mfc.md)

- [동적으로 MFC에 연결된 기본 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC DLL 만들기](../mfc/reference/mfc-dll-wizard.md)

## <a name="see-also"></a>참조

[DLL의 종류](kinds-of-dlls.md)
