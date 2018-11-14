---
title: __getmainargs, __wgetmainargs
ms.date: 11/04/2016
apiname:
- __wgetmainargs
- __getmainargs
apilocation:
- msvcr100.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- __wgetmainargs
- __getmainargs
helpviewer_keywords:
- __wgetmainargs
- __getmainargs
ms.assetid: f72f54eb-9509-4bdf-8752-40fc49055439
ms.openlocfilehash: 6e2bf21f2ac50d3486af56f9581ff6c8d0e0c309
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523340"
---
# <a name="getmainargs-wgetmainargs"></a>__getmainargs, __wgetmainargs

명령줄 구문 분석을 호출하고 전달된 포인터를 통해 다시 `main()`으로 인수를 복사합니다.

## <a name="syntax"></a>구문

```cpp
int __getmainargs(
    int * _Argc,
   char *** _Argv,
   char *** _Env,
   int _DoWildCard,
_startupinfo * _StartInfo);

int __wgetmainargs (
   int *_Argc,
   wchar_t ***_Argv,
   wchar_t ***_Env,
   int _DoWildCard,
   _startupinfo * _StartInfo)
```

#### <a name="parameters"></a>매개 변수

`_Argc`<br/>
`argv` 뒤에 오는 인수 개수를 포함하는 정수입니다. `argc` 매개 변수는 항상 1보다 크거나 같습니다.

`_Argv`<br/>
프로그램의 사용자가 입력한 명령줄 인수를 나타내는 null로 끝나는 문자열의 배열입니다. 규칙에 따라 `argv[0]`는 프로그램 호출에 사용되는 명령이며, argv[1]가 첫 번째 명령줄 인수인 식으로 항상 **NULL**인 argv[argc]까지 진행됩니다. 첫 번째 명령줄 인수는 항상 `argv[1]`이고 마지막 인수는 `argv[argc - 1]`입니다.

`_Env`<br/>
사용자 환경에서 설정되는 변수를 나타내는 문자열 배열입니다. 이 배열은 **NULL** 항목으로 종료됩니다.

`_DoWildCard`<br/>
1로 설정하면 명령줄 인수에서 와일드카드를 확장하고 0으로 설정하면 아무 작업도 수행하지 않는 정수입니다.

`_StartInfo`<br/>
CRT DLL에 전달할 기타 정보입니다.

## <a name="return-value"></a>반환 값

성공하면 0, 실패하면 음수 값입니다.

## <a name="remarks"></a>설명

비와이드 문자 플랫폼에서는 `__getmainargs`를 사용하고 와이드 문자(유니코드) 플랫폼에서는 `__wgetmainargs`를 사용하십시오.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|__getmainargs|internal.h|
|__wgetmainargs|internal.h|