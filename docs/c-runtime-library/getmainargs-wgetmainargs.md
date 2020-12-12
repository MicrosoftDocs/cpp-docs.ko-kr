---
description: '자세히 알아보기: __getmainargs, __wgetmainargs'
title: __getmainargs, __wgetmainargs
ms.date: 11/04/2016
api_name:
- __wgetmainargs
- __getmainargs
api_location:
- msvcr100.dll
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __wgetmainargs
- __getmainargs
helpviewer_keywords:
- __wgetmainargs
- __getmainargs
ms.assetid: f72f54eb-9509-4bdf-8752-40fc49055439
ms.openlocfilehash: 6f06f83a72d037df6a0973b24ac92ecade6c21eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181750"
---
# <a name="__getmainargs-__wgetmainargs"></a>__getmainargs, __wgetmainargs

명령줄 구문 분석을 호출하고 전달된 포인터를 통해 다시 `main()`으로 인수를 복사합니다.

## <a name="syntax"></a>구문

```cpp
int __getmainargs(
    int * _Argc,
   char *** _Argv,
   char **_ _Env,
   int _DoWildCard,
_startupinfo _ _StartInfo);

int __wgetmainargs (
   int *_Argc,
   wchar_t ***_Argv,
   wchar_t **__Env,
   int _DoWildCard,
   _startupinfo _ _StartInfo)
```

#### <a name="parameters"></a>매개 변수

`_Argc`<br/>
`argv` 뒤에 오는 인수 개수를 포함하는 정수입니다. `argc` 매개 변수는 항상 1보다 크거나 같습니다.

`_Argv`<br/>
프로그램의 사용자가 입력한 명령줄 인수를 나타내는 null로 끝나는 문자열의 배열입니다. 규칙에 따라 `argv[0]` 은 프로그램을 호출 하는 데 사용 되는 명령이 며, argv [1]은 첫 번째 명령줄 인수 이므로 항상 **NULL** 인 argv [argc]까지 진행 됩니다. 첫 번째 명령줄 인수는 항상 `argv[1]`이고 마지막 인수는 `argv[argc - 1]`입니다.

`_Env`<br/>
사용자 환경에서 설정되는 변수를 나타내는 문자열 배열입니다. 이 배열은 **NULL** 항목으로 종료 됩니다.

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
