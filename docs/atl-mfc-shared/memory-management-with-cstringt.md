---
title: CStringT를 사용한 메모리 관리
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, memory management
- memory [C++], usage
- IAtlStringMgr class, using
- strings [C++], custom memory management
- CFixedStringT class, description of
- strings [C++], memory management
- CStringT class, memory management
ms.assetid: 88b8342d-19b5-48c4-9cf6-e4c44cece21e
ms.openlocfilehash: af042c80b9e3e0de872261f89255a26728b218cd
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440498"
---
# <a name="memory-management-with-cstringt"></a>CStringT를 사용한 메모리 관리

[CStringT](../atl-mfc-shared/reference/cstringt-class.md) 클래스는 가변 길이 문자열을 조작 하는 데 사용 되는 템플릿 클래스입니다. 이러한 문자열을 저장 하는 메모리는 `CStringT`의 각 인스턴스와 연결 된 문자열 관리자 개체를 통해 할당 및 해제 됩니다. MFC 및 ATL은 다른 문자 형식의 문자열을 조작 하는 `CString`, `CStringA`및 `CStringW`이라는 `CStringT`의 기본 인스턴스화를 제공 합니다. 이러한 문자 형식은 각각 TCHAR.H, **char**및 `wchar_t`형식입니다. 이러한 기본 문자열 형식은 프로세스 힙 (ATL) 또는 CRT 힙 (MFC)에서 메모리를 할당 하는 문자열 관리자를 사용 합니다. 일반적인 응용 프로그램의 경우이 메모리 할당 스키마로 충분 합니다. 그러나 문자열이 나 다중 스레드 코드를 집중적으로 사용 하는 코드의 경우 기본 메모리 관리자가 최적으로 수행 되지 않을 수 있습니다. 이 항목에서는 `CStringT`의 기본 메모리 관리 동작을 재정의 하 여 현재 작업에 대해 특별히 최적화 된 할당자를 만드는 방법에 대해 설명 합니다.

- [사용자 지정 문자열 관리자 구현(기본 방법)](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)

- [힙 경합 방지](../atl-mfc-shared/avoidance-of-heap-contention.md)

- [사용자 지정 문자열 관리자 구현(고급 방법)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)

- [CFixedStringT: 사용자 지정 문자열 관리자의 예](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)

## <a name="see-also"></a>참고 항목

[CustomString 샘플](../overview/visual-cpp-samples.md)
