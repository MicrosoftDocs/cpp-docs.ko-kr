---
description: '자세한 정보: Delay-Loaded DLL 언로드'
title: 지연 로드된 DLL 언로드
ms.date: 11/04/2016
helpviewer_keywords:
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
ms.openlocfilehash: fd733bfa02a6d90eecb1b617288d368d33766282
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178942"
---
# <a name="unloading-a-delay-loaded-dll"></a>지연 로드된 DLL 언로드

기본 제공 지연 로드 도우미는 지연 로드 설명자에 pUnloadIAT 필드의 원래 IAT (가져오기 주소 테이블)에 대 한 포인터와 복사본이 있는지 확인 합니다. 이 경우 목록에 포인터를 가져오기 지연 설명자에 저장 합니다. 이를 통해 도우미 함수는 이름으로 DLL을 검색 하 여 해당 DLL의 언로드를 명시적으로 지원할 수 있습니다.

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

UnloadInfo 구조체는 **Localalloc** 및 **LocalFree** 구현을 각각 연산자와 연산자로 사용 하는 c + + 클래스를 사용 하 여 구현 됩니다 **`new`** **`delete`** . 이러한 옵션은 __puiHead를 사용 하 여 목록의 맨 위에 있는 표준 연결 된 목록에 유지 됩니다.

__FUnloadDelayLoadedDLL를 호출 하면 로드 된 Dll 목록에서 제공 하는 이름을 찾으려고 합니다. 정확한 일치는 필수 항목입니다. 발견 된 경우 pUnloadIAT의 IAT 복사본이 실행 중인 IAT의 맨 위에 복사 되어 썽크 포인터가 복원 되며, 라이브러리가 **Freelibrary** 로 해제 되 고, 일치 하는 **UnloadInfo** 레코드가 목록에서 연결 해제 되 고, TRUE가 반환 됩니다.

__FUnloadDelayLoadedDLL2 함수에 대 한 인수는 대/소문자를 구분 합니다. 예를 들어 다음을 지정 합니다.

```cpp
__FUnloadDelayLoadedDLL2("user32.DLL");
```

그렇지 않음:

```cpp
__FUnloadDelayLoadedDLL2("User32.DLL");.
```

## <a name="see-also"></a>참고 항목

[도우미 함수 이해](understanding-the-helper-function.md)
