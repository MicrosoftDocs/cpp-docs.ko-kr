---
description: '자세한 정보: 구조 및 상수 정의'
title: 구조체 및 상수 정의
ms.date: 11/04/2016
ms.assetid: 1df7cf46-b853-4788-a257-100d5c37997f
ms.openlocfilehash: 5a9e372815e25883cf69497c77388002a7015572
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230330"
---
# <a name="structure-and-constant-definitions"></a>구조체 및 상수 정의

기본 도우미 루틴은 여러 구조체를 사용 하 여 후크 함수와 통신 하 고 모든 예외를 처리 합니다. 다음은 후크에 전달 되는 알림 및 오류 값, 정보 구조 및 포인터 대 후크 함수 형식입니다.

```
//
// Delay load import hook notifications
//
enum {
    dliStartProcessing,        // used to bypass or note helper only
    dliNotePreLoadLibrary,     // called just before LoadLibrary, can
                               //  override w/ new HMODULE return val
    dliNotePreGetProcAddress,  // called just before GetProcAddress, can
                               //  override w/ new FARPROC return value
    dliFailLoadLib,            // failed to load library, fix it by
                               //  returning a valid HMODULE
    dliFailGetProc,            // failed to get proc address, fix it by
                               //  returning a valid FARPROC
    dliNoteEndProcessing,      // called after all processing is done, no
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
    DWORD           cb;         // size of structure
    PCImgDelayDescr pidd;       // raw form of data (everything is there)
    FARPROC *       ppfn;       // points to address of function to load
    LPCSTR          szDll;      // name of dll
    DelayLoadProc   dlp;        // name or ordinal of procedure
    HMODULE         hmodCur;    // the hInstance of the library we have loaded
    FARPROC         pfnCur;     // the actual function that will be called
    DWORD           dwLastError;// error received (if an error notification)
    } DelayLoadInfo, * PDelayLoadInfo;

typedef FARPROC (WINAPI *PfnDliHook)(
    unsigned        dliNotify,
    PDelayLoadInfo  pdli
    );

typedef struct ImgDelayDescr {
    DWORD        grAttrs;        // attributes
    RVA          rvaDLLName;     // RVA to dll name
    RVA          rvaHmod;        // RVA of module handle
    RVA          rvaIAT;         // RVA of the IAT
    RVA          rvaINT;         // RVA of the INT
    RVA          rvaBoundIAT;    // RVA of the optional bound IAT
    RVA          rvaUnloadIAT;   // RVA of optional copy of original IAT
    DWORD        dwTimeStamp;    // 0 if not bound,
                                 // O.W. date/time stamp of DLL bound to (Old BIND)
    } ImgDelayDescr, * PImgDelayDescr;
```

## <a name="see-also"></a>참고 항목

[도우미 함수 이해](understanding-the-helper-function.md)
