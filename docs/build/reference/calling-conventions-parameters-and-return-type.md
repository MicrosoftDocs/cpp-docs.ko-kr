---
description: '자세한 정보: 지연 로드 호출 규칙, 매개 변수 및 반환 형식'
title: 호출 규칙, 매개 변수, 반환 형식
ms.date: 01/19/2021
helpviewer_keywords:
- calling conventions, helper functions
- helper functions, calling conventions
- helper functions, return types
ms.openlocfilehash: 68817f2746abccf9ad6ae72c4f189fa29aa4c26f
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98666929"
---
# <a name="delay-load-helper-calling-conventions-parameters-and-return-type"></a>부하 도우미 호출 규칙, 매개 변수 및 반환 형식 지연

지연 로드 도우미 루틴의 프로토타입은 다음과 같습니다.

```C
FARPROC WINAPI __delayLoadHelper2(
    PCImgDelayDescr pidd,
    FARPROC * ppfnIATEntry
);
```

## <a name="parameters"></a>매개 변수

*`pidd`*<br/>
**`const`** `ImgDelayDescr` 다양 한 가져오기 관련 데이터의 오프셋, 바인딩 정보에 대 한 타임 스탬프 및 설명자 콘텐츠에 대 한 추가 정보를 제공 하는 특성 집합을 포함 하는에 대 한 포인터입니다. 현재 `dlattrRva` 설명자의 주소가 상대 가상 주소 임을 나타내는 특성은 하나 뿐입니다. 자세한 내용은의 선언을 참조 하세요 *`delayimp.h`* .

구조체에 대 한 정의는 `PCImgDelayDescr` [구조체 및 상수 정의](structure-and-constant-definitions.md)를 참조 하세요.

*`ppfnIATEntry`*<br/>
지연 로드 가져오기 주소 테이블 (IAT)의 슬롯에 대 한 포인터입니다. 가져온 함수의 주소로 업데이트 되는 슬롯입니다. 도우미 루틴은 반환 하는 것과 동일한 값을이 위치에 저장 해야 합니다.

## <a name="expected-return-values"></a>반환 값이 필요 합니다.

함수에 성공하면 가져온 함수의 주소가 반환됩니다.

함수가 실패 하면 구조화 된 예외가 발생 하 고 0이 반환 됩니다. 다음과 같은 3가지 형식의 예외가 발생할 수 있습니다.

- 의 특성이 올바르게 지정 되지 않은 경우에 발생 하는 잘못 된 매개 변수 *`pidd`* 입니다.

- 지정된 DLL에서 실패한 `LoadLibrary`

- `GetProcAddress`의 실패

이러한 예외를 처리 하는 것은 사용자의 책임입니다.

## <a name="remarks"></a>설명

도우미 함수에 대 한 호출 규칙은 **`__stdcall`** 입니다. 반환 값의 형식은 관련이 없으므로 `FARPROC` 이 사용 됩니다. 이 함수에는 C 링크를 사용 합니다. 즉, c + + 코드로 선언 된 경우에는이 링크를 래핑해야 `extern "C"` 합니다. `ExternC`매크로는이 래퍼를 처리 합니다.

도우미 루틴을 알림 후크에 사용 하려는 경우가 아니면 전달 된 함수 포인터 위치에 도우미 함수의 반환 값을 저장 합니다. 이러한 경우 사용자 코드가 반환할 적절한 함수 포인터 찾기를 담당합니다. 그러면 링커가 생성한 썽크 코드가 해당 반환 값을 가져오기의 실제 대상으로 인식하여 해당 대상으로 직접 이동합니다.

## <a name="sample"></a>샘플

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
            // If you choose you may handle the failure by returning
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

## <a name="see-also"></a>참고 항목

[도우미 함수 이해](understanding-the-helper-function.md)
