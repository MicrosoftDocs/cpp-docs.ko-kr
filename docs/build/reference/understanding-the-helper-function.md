---
description: 지연 로드 도우미 함수에 대 한 자세한 정보
title: 지연 로드 도우미 함수 이해
ms.date: 01/19/2021
helpviewer_keywords:
- delayed loading of DLLs, helper function
- __delayLoadHelper2 function
- delayimp.lib
- __delayLoadHelper function
- delayhlp.cpp
- delayimp.h
- helper functions
ms.openlocfilehash: 6108e896b6d7a370f2b4d6ab8f5baa880112a21e
ms.sourcegitcommit: c20734f18d3d49bb38b1628c68b53b54b3eeeb03
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99522744"
---
# <a name="understand-the-delay-load-helper-function"></a>지연 로드 도우미 함수 이해

링커 지원 지연 로드에 대 한 도우미 함수는 런타임에 실제로 DLL을 로드 하는 것입니다. 도우미 함수를 수정 하 여 동작을 사용자 지정할 수 있습니다. 에서 제공 된 도우미 함수를 사용 하는 대신 *`delayimp.lib`* 고유한 함수를 작성 하 고 프로그램에 연결 합니다. 하나의 도우미 함수는 모든 지연 로드 된 Dll을 사용 합니다.

DLL 또는 가져오기의 이름을 기반으로 특정 처리를 수행 하려는 경우 자체 버전의 도우미 함수를 제공할 수 있습니다.

도우미 함수는 다음 작업을 수행 합니다.

- 라이브러리에 대 한 저장 된 핸들이 이미 로드 되었는지 확인 합니다.

- `LoadLibrary`를 호출 하 여 DLL 로드를 시도 합니다.

- `GetProcAddress`프로시저의 주소를 가져오기 위해를 호출 합니다.

- 지연 가져오기 로드 썽크로 반환 되어 현재 로드 된 진입점을 호출 합니다.

도우미 함수는 다음 작업을 수행할 때마다 프로그램의 알림 후크를 다시 호출할 수 있습니다.

- 도우미 함수가 시작 될 때

- `LoadLibrary`도우미 함수에서가 호출 되기 직전

- `GetProcAddress`도우미 함수에서가 호출 되기 직전

- 도우미 함수에서에 대 한 호출이 `LoadLibrary` 실패 하면

- 도우미 함수에서에 대 한 호출이 `GetProcAddress` 실패 하면

- 도우미 함수 처리가 완료 된 후

이러한 각 후크 지점은 지연 가져오기 로드 썽크로의 반환을 제외 하 고 특정 방식으로 도우미 루틴의 정상적인 처리를 변경 하는 값을 반환할 수 있습니다.

기본 도우미 코드는 *`delayhlp.cpp`* 및 MSVC 디렉터리에서 찾을 수 있습니다 *`delayimp.h`* *`include`* . *`delayimp.lib`* *`lib`* 대상 아키텍처에 대 한 MSVC 디렉터리에서로 컴파일됩니다. 사용자 고유의 도우미 함수를 작성 하지 않는 한이 라이브러리를 컴파일에 포함 해야 합니다.

## <a name="delay-load-helper-calling-conventions-parameters-and-return-type"></a><a name="calling-conventions-parameters-and-return-type"></a> 부하 도우미 호출 규칙, 매개 변수 및 반환 형식 지연

지연 로드 도우미 루틴의 프로토타입은 다음과 같습니다.

```C
FARPROC WINAPI __delayLoadHelper2(
    PCImgDelayDescr pidd,
    FARPROC * ppfnIATEntry
);
```

### <a name="parameters"></a>매개 변수

*`pidd`*\
**`const`** `ImgDelayDescr` 다양 한 가져오기 관련 데이터의 오프셋, 바인딩 정보에 대 한 타임 스탬프 및 설명자 콘텐츠에 대 한 추가 정보를 제공 하는 특성 집합을 포함 하는에 대 한 포인터입니다. 현재 `dlattrRva` 설명자의 주소가 상대 가상 주소 임을 나타내는 특성은 하나 뿐입니다. 자세한 내용은의 선언을 참조 하세요 *`delayimp.h`* .

지연 설명자의 포인터 ()는 `ImgDelayDescr` *`delayimp.h`* rva (상대 가상 주소)를 사용 하 여 32 비트 및 64 비트 프로그램 모두에서 예상 대로 작동 합니다. 이를 사용 하려면에 있는 함수를 사용 하 여 이러한 Rva를 다시 포인터로 변환 `PFromRva` *`delayhlp.cpp`* 합니다. 설명자의 각 필드에 대해이 함수를 사용 하 여 32 비트 또는 64 비트 포인터로 다시 변환할 수 있습니다. 기본 지연 로드 도우미 함수는 예제로 사용 하기에 적합 한 템플릿입니다.

구조체에 대 한 정의는 `PCImgDelayDescr` [구조체 및 상수 정의](#structure-and-constant-definitions)를 참조 하세요.

*`ppfnIATEntry`*\
지연 로드 가져오기 주소 테이블 (IAT)의 슬롯에 대 한 포인터입니다. 가져온 함수의 주소로 업데이트 되는 슬롯입니다. 도우미 루틴은 반환 하는 것과 동일한 값을이 위치에 저장 해야 합니다.

### <a name="expected-return-values"></a>반환 값이 필요 합니다.

도우미 함수가 성공 하면 가져온 함수의 주소를 반환 합니다.

함수가 실패 하면 구조화 된 예외가 발생 하 고 0이 반환 됩니다. 다음과 같은 3가지 형식의 예외가 발생할 수 있습니다.

- 의 특성이 올바르게 지정 되지 않은 경우에 발생 하는 잘못 된 매개 변수 *`pidd`* 입니다. 이를 복구할 수 없는 오류로 처리 합니다.

- 지정된 DLL에서 실패한 `LoadLibrary`

- `GetProcAddress`의 실패

이러한 예외를 처리 하는 것은 사용자의 책임입니다. 자세한 내용은 [오류 처리 및 알림](error-handling-and-notification.md)을 참조 하세요.

### <a name="remarks"></a>설명

도우미 함수에 대 한 호출 규칙은 **`__stdcall`** 입니다. 반환 값의 형식은 관련이 없으므로 `FARPROC` 이 사용 됩니다. 이 함수에는 C 링크를 사용 합니다. 즉, c + + 코드로 선언 된 경우에는이 링크를 래핑해야 `extern "C"` 합니다. `ExternC`매크로는이 래퍼를 처리 합니다.

도우미 루틴을 알림 후크에 사용 하려면 코드에서 반환할 적절 한 함수 포인터를 지정 해야 합니다. 그러면 링커가 생성한 썽크 코드가 해당 반환 값을 가져오기의 실제 대상으로 인식하여 해당 대상으로 직접 이동합니다. 도우미 루틴을 알림 후크에 사용 하지 않으려면 도우미 함수의 반환 값 `ppfnIATEntry` 을 전달 된 함수 포인터 위치에 저장 합니다.

## <a name="sample-hook-function"></a>Sample 후크 함수

다음 코드에서는 기본 후크 함수를 구현 하는 방법을 보여 줍니다.

```C
FARPROC WINAPI delayHook(unsigned dliNotify, PDelayLoadInfo pdli)
{
    switch (dliNotify) {
        case dliStartProcessing :

            // If you want to return control to the helper, return 0.
            // Otherwise, return a pointer to a FARPROC helper function
            // that will be used instead, thereby bypassing the rest
            // of the helper.

            break;

        case dliNotePreLoadLibrary :

            // If you want to return control to the helper, return 0.
            // Otherwise, return your own HMODULE to be used by the
            // helper instead of having it call LoadLibrary itself.

            break;

        case dliNotePreGetProcAddress :

            // If you want to return control to the helper, return 0.
            // If you choose you may supply your own FARPROC function
            // address and bypass the helper's call to GetProcAddress.

            break;

        case dliFailLoadLib :

            // LoadLibrary failed.
            // If you don't want to handle this failure yourself, return 0.
            // In this case the helper will raise an exception
            // (ERROR_MOD_NOT_FOUND) and exit.
            // If you want to handle the failure by loading an alternate
            // DLL (for example), then return the HMODULE for
            // the alternate DLL. The helper will continue execution with
            // this alternate DLL and attempt to find the
            // requested entrypoint via GetProcAddress.

            break;

        case dliFailGetProc :

            // GetProcAddress failed.
            // If you don't want to handle this failure yourself, return 0.
            // In this case the helper will raise an exception
            // (ERROR_PROC_NOT_FOUND) and exit.
            // If you choose, you may handle the failure by returning
            // an alternate FARPROC function address.

            break;

        case dliNoteEndProcessing :

            // This notification is called after all processing is done.
            // There is no opportunity for modifying the helper's behavior
            // at this point except by longjmp()/throw()/RaiseException.
            // No return value is processed.

            break;

        default :

            return NULL;
    }

    return NULL;
}

/*
and then at global scope somewhere:

ExternC const PfnDliHook __pfnDliNotifyHook2 = delayHook;
ExternC const PfnDliHook __pfnDliFailureHook2 = delayHook;
*/
```

## <a name="delay-load-structure-and-constant-definitions"></a><a name="structure-and-constant-definitions"></a> 지연 로드 구조 및 상수 정의

기본 지연 로드 도우미 루틴은 여러 구조체를 사용 하 여 후크 함수와 통신 하 고 예외를 발생 시킵니다. 이러한 구조는에 정의 되어 *`delayimp.h`* 있습니다. 다음은 후크에 전달 되는 매크로, 형식 정의, 알림 및 오류 값, 정보 구조 및 후크 포인터 함수 형식입니다.

```C
#define _DELAY_IMP_VER  2

#if defined(__cplusplus)
#define ExternC extern "C"
#else
#define ExternC extern
#endif

typedef IMAGE_THUNK_DATA *          PImgThunkData;
typedef const IMAGE_THUNK_DATA *    PCImgThunkData;
typedef DWORD                       RVA;

typedef struct ImgDelayDescr {
    DWORD           grAttrs;        // attributes
    RVA             rvaDLLName;     // RVA to dll name
    RVA             rvaHmod;        // RVA of module handle
    RVA             rvaIAT;         // RVA of the IAT
    RVA             rvaINT;         // RVA of the INT
    RVA             rvaBoundIAT;    // RVA of the optional bound IAT
    RVA             rvaUnloadIAT;   // RVA of optional copy of original IAT
    DWORD           dwTimeStamp;    // 0 if not bound,
                                    // O.W. date/time stamp of DLL bound to (Old BIND)
    } ImgDelayDescr, * PImgDelayDescr;

typedef const ImgDelayDescr *   PCImgDelayDescr;

enum DLAttr {                   // Delay Load Attributes
    dlattrRva = 0x1,                // RVAs are used instead of pointers
                                    // Having this set indicates a VC7.0
                                    // and above delay load descriptor.
    };

//
// Delay load import hook notifications
//
enum {
    dliStartProcessing,             // used to bypass or note helper only
    dliNoteStartProcessing = dliStartProcessing,

    dliNotePreLoadLibrary,          // called just before LoadLibrary, can
                                    //  override w/ new HMODULE return val
    dliNotePreGetProcAddress,       // called just before GetProcAddress, can
                                    //  override w/ new FARPROC return value
    dliFailLoadLib,                 // failed to load library, fix it by
                                    //  returning a valid HMODULE
    dliFailGetProc,                 // failed to get proc address, fix it by
                                    //  returning a valid FARPROC
    dliNoteEndProcessing,           // called after all processing is done, no
                                    //  bypass possible at this point except
                                    //  by longjmp()/throw()/RaiseException.
    };

typedef struct DelayLoadProc {
    BOOL                fImportByName;
    union {
        LPCSTR          szProcName;
        DWORD           dwOrdinal;
        };
    } DelayLoadProc;

typedef struct DelayLoadInfo {
    DWORD               cb;         // size of structure
    PCImgDelayDescr     pidd;       // raw form of data (everything is there)
    FARPROC *           ppfn;       // points to address of function to load
    LPCSTR              szDll;      // name of dll
    DelayLoadProc       dlp;        // name or ordinal of procedure
    HMODULE             hmodCur;    // the hInstance of the library we have loaded
    FARPROC             pfnCur;     // the actual function that will be called
    DWORD               dwLastError;// error received (if an error notification)
    } DelayLoadInfo, * PDelayLoadInfo;

typedef FARPROC (WINAPI *PfnDliHook)(
    unsigned        dliNotify,
    PDelayLoadInfo  pdli
    );
```

## <a name="calculate-necessary-values-for-delay-loading"></a><a name="calculate-necessary-values"></a> 지연 로드에 필요한 값 계산

지연 로드 도우미 루틴은 두 가지 중요 한 정보를 계산 해야 합니다. 이 정보를 계산 하는 데에는 두 가지 인라인 함수가 있습니다 *`delayhlp.cpp`* .

- 첫 번째는 `IndexFromPImgThunkData` 세 개의 다른 테이블 (가져오기 주소 테이블 (IAT), 바운드 가져오기 주소 테이블 (BIAT) 및 바인딩되지 않은 가져오기 주소 테이블 (UIAT))에 대 한 현재 가져오기의 인덱스를 계산 합니다.

- 두 번째는 `CountOfImports` 유효한 IAT의 가져오기 수를 계산 합니다.

```C
// utility function for calculating the index of the current import
// for all the tables (INT, BIAT, UIAT, and IAT).
__inline unsigned
IndexFromPImgThunkData(PCImgThunkData pitdCur, PCImgThunkData pitdBase) {
    return pitdCur - pitdBase;
    }

// utility function for calculating the count of imports given the base
// of the IAT. NB: this only works on a valid IAT!
__inline unsigned
CountOfImports(PCImgThunkData pitdBase) {
    unsigned        cRet = 0;
    PCImgThunkData  pitd = pitdBase;
    while (pitd->u1.Function) {
        pitd++;
        cRet++;
        }
    return cRet;
    }
```

## <a name="support-unload-of-a-delay-loaded-dll"></a><a name="unload-a-delay-loaded-dll"></a> 지연 로드 된 DLL의 언로드 지원

지연 로드 된 DLL이 로드 될 때 기본 지연 로드 도우미는 지연 로드 설명자에 포인터와 필드의 원래 IAT (가져오기 주소 테이블) 복사본이 있는지 확인 합니다 `pUnloadIAT` . 그렇다면 도우미는 목록에 포인터를 가져오기 지연 설명자에 저장 합니다. 이 항목을 통해 도우미 함수는 dll을 이름별로 검색 하 여 해당 DLL의 언로드를 명시적으로 지원할 수 있습니다.

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
__FUnloadDelayLoadedDLL2("User32.DLL");
```

지연 로드 된 DLL을 언로드하는 예제는 [지연 로드 된 dll의 명시적 언로드](linker-support-for-delay-loaded-dlls.md)를 참조 하세요.

## <a name="develop-your-own-delay-load-helper-function"></a><a name="develop-your-own-helper-function"></a> 사용자 고유의 지연 로드 도우미 함수 개발

사용자 고유의 지연 로드 도우미 루틴을 제공 하는 것이 좋습니다. 사용자의 루틴에서 DLL 또는 가져오기의 이름을 기준으로 특정 처리를 수행할 수 있습니다. 사용자 고유의 코드를 삽입 하는 방법에는 두 가지가 있습니다. 제공 된 코드를 기반으로 사용자 고유의 도우미 함수를 코딩 합니다. 또는 제공 된 도우미를 후크하여 [알림 후크](error-handling-and-notification.md#notification-hooks)를 사용 하 여 고유한 함수를 호출 합니다.

### <a name="code-your-own-helper"></a>사용자 고유의 도우미 코딩

사용자 고유의 도우미 루틴을 만드는 것은 간단 합니다. 새 함수에 대 한 지침으로 기존 코드를 사용할 수 있습니다. 함수는 기존 도우미와 동일한 호출 규칙을 사용 해야 합니다. 그리고 링커 생성 썽크로 반환 되는 경우 적절 한 함수 포인터를 반환 해야 합니다. 코드를 만든 후 호출을 충족 하거나 호출을 받을 수 있습니다.

### <a name="use-the-start-processing-notification-hook"></a>처리 시작 알림 후크 사용

알림의 기본 도우미와 동일한 값을 사용 하는 사용자 제공 알림 후크 함수에 대 한 새 포인터를 제공 하는 것이 가장 쉽습니다 `dliStartProcessing` . 이 시점에서 기본 도우미가 성공적으로 반환 되 면 기본 도우미의 모든 추가 처리를 무시 하므로 후크 함수는 기본적으로 새 도우미 함수가 될 수 있습니다.

## <a name="see-also"></a>참고 항목

[링커의 지연 로드된 DLL 지원](linker-support-for-delay-loaded-dlls.md#explicitly-unload-a-delay-loaded-dll)
