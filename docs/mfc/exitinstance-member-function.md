---
title: ExitInstance 멤버 함수
ms.date: 11/04/2016
f1_keywords: []
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
ms.openlocfilehash: 58546d26293ad48a39a36b98ba4bfdabb68385ee
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622691"
---
# <a name="exitinstance-member-function"></a>ExitInstance 멤버 함수

[CWinApp](reference/cwinapp-class.md) 클래스의 [exitinstance](reference/cwinapp-class.md#exitinstance) 멤버 함수는 응용 프로그램 복사본이 종료 될 때마다 (일반적으로 사용자가 응용 프로그램을 종료 한 결과로) 호출 됩니다.

`ExitInstance`GDI (그래픽 장치 인터페이스) 리소스를 해제 하거나 프로그램 실행 중에 사용 되는 메모리의 할당을 취소 하는 등 특별 한 정리 처리가 필요한 경우 재정의 합니다. 그러나 문서 및 뷰와 같은 표준 항목의 정리는 프레임 워크에서 제공 되며, 해당 개체와 관련 된 특수 한 정리를 수행 하기 위한 재정의 가능한 다른 함수도 제공 합니다.

## <a name="see-also"></a>참고 항목

[CWinApp: 애플리케이션 클래스](cwinapp-the-application-class.md)
