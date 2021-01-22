---
description: 지연 로드 된 DLL 언로드에 대해 자세히 알아보기
title: 지연 로드 된 DLL 언로드
ms.date: 01/19/2021
helpviewer_keywords:
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.openlocfilehash: 2ac898d56609ebb3aadc57ea8df00fa63fcbc3f0
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98667239"
---
# <a name="unload-a-delay-loaded-dll"></a>지연 로드 된 DLL 언로드

기본 지연 로드 도우미는 지연 로드 설명자에 포인터와 필드의 원래 IAT (가져오기 주소 테이블) 복사본이 있는지 확인 합니다 `pUnloadIAT` . 그렇다면 도우미는 목록에 포인터를 가져오기 지연 설명자에 저장 합니다. 이 항목을 통해 도우미 함수는 dll을 이름별로 검색 하 여 해당 DLL의 언로드를 명시적으로 지원할 수 있습니다.

다음은 지연 로드 된 DLL의 명시적 언로드를 위한 관련 구조 및 함수입니다.

```cpp
//
// Unload support from delayimp.h
//

// routine definition; takes a pointer to a name to unload

ExternC
BOOL WINAPI
__FUnloadDelayLoadedDLL2(LPCSTR szDll);

// structure definitions for the list of unload records
typedef struct UnloadInfo * PUnloadInfo;
typedef struct UnloadInfo {
    PUnloadInfo     puiNext;
    PCImgDelayDescr pidd;
    } UnloadInfo;

// from delayhlp.cpp
// the default delay load helper places the unloadinfo records in the
// list headed by the following pointer.
ExternC
PUnloadInfo __puiHead;
```

`UnloadInfo`구조체는 `LocalAlloc` 및 `LocalFree` 구현을 `operator new` 각각 및로 사용 하는 c + + 클래스를 사용 하 여 구현 됩니다 `operator delete` . 이러한 옵션은를 목록의 헤드로 사용 하는 표준 연결 된 목록에 유지 됩니다 `__puiHead` .

를 호출 하면 `__FUnloadDelayLoadedDLL` 로드 된 dll 목록에서 제공 하는 이름을 찾으려고 합니다. 정확 하 게 일치 해야 합니다. 검색 된 경우에서 IAT의 복사본이 `pUnloadIAT` 실행 중인 iat의 맨 위에 복사 되어 썽크 포인터가 복원 됩니다. 그런 다음를 사용 하 여 라이브러리를 해제 하 고 `FreeLibrary` , 일치 레코드를 목록에서 연결 해제 하 `UnloadInfo` 고 삭제 한 후 `TRUE` 반환 됩니다.

함수에 대 한 인수는 `__FUnloadDelayLoadedDLL2` 대/소문자를 구분 합니다. 예를 들어 다음을 지정 합니다.

```cpp
__FUnloadDelayLoadedDLL2("user32.dll");
```

그렇지 않음:

```cpp
__FUnloadDelayLoadedDLL2("User32.DLL");.
```

## <a name="see-also"></a>참고 항목

[도우미 함수 이해](understanding-the-helper-function.md)
