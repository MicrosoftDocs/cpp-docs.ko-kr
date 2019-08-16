---
title: 사용자 지정 문자열 관리자 구현 (기본 방법)
ms.date: 11/04/2016
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
ms.openlocfilehash: 92c1c46f5251980f9cefb55e052e9aff395e0e60
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491312"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>사용자 지정 문자열 관리자 구현 (기본 방법)

문자열 데이터에 대 한 메모리 할당 체계를 사용자 지정 하는 가장 쉬운 방법은 ATL 제공 `CAtlStringMgr` 클래스를 사용 하는 것 이지만 사용자 고유의 메모리 할당 루틴을 제공 하는 것입니다. 생성자 `CAtlStringMgr` 는 단일 매개 변수 ( `IAtlMemMgr` 개체에 대 한 포인터)를 사용 합니다. `IAtlMemMgr`는 힙에 대 한 제네릭 인터페이스를 제공 하는 추상 기본 클래스입니다. `IAtlMemMgr` 는`CAtlStringMgr` 인터페이스를 사용 하 여 문자열 데이터를 저장 하는 데 사용 되는 메모리를 할당, 다시 할당 및 해제 합니다. 인터페이스를 `IAtlMemMgr` 직접 구현 하거나 ATL에서 제공 하는 5 개의 메모리 관리자 클래스 중 하나를 사용할 수 있습니다. ATL 제공 메모리 관리자는 단순히 기존 메모리 할당 기능을 래핑합니다.

- [Ccrtheap](../atl/reference/ccrtheap-class.md) 표준 CRT 힙 함수 ([malloc](../c-runtime-library/reference/malloc.md), [free](../c-runtime-library/reference/free.md)및 [realloc](../c-runtime-library/reference/realloc.md))를 래핑합니다.

- [CWin32Heap](../atl/reference/cwin32heap-class.md) [Heapalloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc), [Heapalloc](/windows/win32/api/heapapi/nf-heapapi-heapfree)및 [HeapRealloc](/windows/win32/api/heapapi/nf-heapapi-heaprealloc) 를 사용 하 여 Win32 힙 핸들을 래핑합니다.

- [Clocalheap](../atl/reference/clocalheap-class.md) Win32 Api를 래핑합니다. [Localalloc](/windows/win32/api/winbase/nf-winbase-localalloc), [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree)및 [LocalRealloc](/windows/win32/api/winbase/nf-winbase-localrealloc)

- [Cglobalheap](../atl/reference/cglobalheap-class.md) Win32 Api를 래핑합니다. [Globalalloc](/windows/win32/api/winbase/nf-winbase-globalalloc), [Globalalloc](/windows/win32/api/winbase/nf-winbase-globalfree)및 [GlobalRealloc](/windows/win32/api/winbase/nf-winbase-globalrealloc).

- [CComHeap](../atl/reference/ccomheap-class.md) COM 태스크 할당자 Api를 래핑합니다. [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc), [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree)및 [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc)

문자열 메모리 관리를 위해 가장 유용 하 게 사용할 수 있는 클래스 `CWin32Heap` 는 여러 개의 독립적인 힙을 만들 수 있기 때문입니다. 예를 들어 문자열에 대해서만 별도의 힙을 사용 하려는 경우 다음을 수행할 수 있습니다.

[!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]

이 개인 문자열 관리자를 사용 하 여 `CString` 변수에 대 한 메모리를 관리 하려면 관리자에 대 한 포인터를 변수의 생성자 `CString` 에 매개 변수로 전달 합니다.

[!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]

## <a name="see-also"></a>참고자료

[CStringT를 사용한 메모리 관리](../atl-mfc-shared/memory-management-with-cstringt.md)
