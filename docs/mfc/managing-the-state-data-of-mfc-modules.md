---
description: '자세한 정보: MFC 모듈의 상태 데이터 관리'
title: MFC 모듈의 상태 데이터 관리
ms.date: 11/19/2018
helpviewer_keywords:
- global state [MFC]
- data management [MFC], MFC modules
- window procedure entry points [MFC]
- exported interfaces and global state [MFC]
- module states [MFC], saving and restoring
- data management [MFC]
- MFC, managing state data
- multiple modules [MFC]
- module state restored [MFC]
ms.assetid: 81889c11-0101-4a66-ab3c-f81cf199e1bb
ms.openlocfilehash: e991e73b40f49f3be4630c26957c827aa6f1bf0b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228029"
---
# <a name="managing-the-state-data-of-mfc-modules"></a>MFC 모듈의 상태 데이터 관리

이 문서에서는 MFC 모듈의 상태 데이터 및 실행 흐름 (실행 시 응용 프로그램을 통해 실행 되는 경로 코드)이 모듈을 나갈 때이 상태가 업데이트 되는 방법에 대해 설명 합니다. AFX_MANAGE_STATE 및 METHOD_PROLOGUE 매크로를 사용 하 여 모듈 상태를 전환 하는 방법도 설명 합니다.

> [!NOTE]
> 여기에서 "모듈" 이란 용어는 응용 프로그램의 나머지 부분과 독립적으로 작동 하지만 MFC DLL의 공유 복사본을 사용 하는 DLL 또는 dll 집합을 참조 합니다. ActiveX 컨트롤은 모듈의 일반적인 예입니다.

다음 그림에 표시 된 것 처럼 MFC는 응용 프로그램에서 사용 되는 각 모듈에 대 한 상태 데이터를 포함 합니다. 이러한 데이터의 예로는 Windows 인스턴스 핸들 (리소스를 로드 하는 데 사용), `CWinApp` 응용 프로그램의 현재 및 개체에 대 한 포인터 `CWinThread` , OLE 모듈 참조 횟수 및 windows 개체 핸들과 해당 MFC 개체의 해당 인스턴스 간의 연결을 유지 관리 하는 다양 한 맵이 있습니다. 그러나 응용 프로그램에서 여러 모듈을 사용 하는 경우 각 모듈의 상태 데이터는 응용 프로그램 너비가 아닙니다. 대신 각 모듈에는 MFC의 상태 데이터에 대 한 자체 개인 복사본이 있습니다.

![응용 프로그램&#41;&#40;단일 모듈의 상태 데이터 ](../mfc/media/vc387n1.gif "응용 프로그램&#41; &#40;단일 모듈의 상태 데이터") <br/>
단일 모듈(애플리케이션)의 상태 데이터

모듈의 상태 데이터는 구조에 포함 되며 항상 해당 구조체에 대 한 포인터를 통해 사용할 수 있습니다. 다음 그림에 표시 된 것 처럼 실행 흐름이 특정 모듈에 들어가면 해당 모듈의 상태가 "current" 또는 "유효" 상태 여야 합니다. 따라서 각 스레드 개체에는 해당 응용 프로그램의 유효 상태 구조에 대 한 포인터가 있습니다. 이 포인터를 항상 업데이트 된 상태로 유지 하는 것은 응용 프로그램의 전역 상태를 관리 하 고 각 모듈 상태의 무결성을 유지 관리 하는 데 중요 합니다. 전역 상태를 잘못 관리 하면 예기치 않은 응용 프로그램 동작이 발생할 수 있습니다.

![여러 모듈의 상태 데이터](../mfc/media/vc387n2.gif "여러 모듈 상태 데이터") <br/>
여러 모듈의 상태 데이터

즉, 각 모듈은 모든 진입점에서 모듈 상태를 올바르게 전환 하는 일을 담당 합니다. "진입점"은 실행 흐름이 모듈의 코드를 입력할 수 있는 위치입니다. 진입점은 다음과 같습니다.

- [DLL의 내보낸 함수](exported-dll-function-entry-points.md)

- [COM 인터페이스의 멤버 함수](com-interface-entry-points.md)

- [창 프로시저](window-procedure-entry-points.md)

## <a name="see-also"></a>참고 항목

[일반 MFC 항목](general-mfc-topics.md)
