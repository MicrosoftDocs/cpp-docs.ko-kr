---
description: '자세히 알아보기: _ismbbalpha, _ismbbalpha_l'
title: _ismbbalpha, _ismbbalpha_l
ms.date: 4/2/2020
api_name:
- _ismbbalpha
- _ismbbalpha_l
- _o__ismbbalpha
- _o__ismbbalpha_l
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ismbbalpha
- ismbbalpha_l
- _ismbbalpha
- _ismbbalpha_l
helpviewer_keywords:
- ismbbalpha function
- ismbbalpha_l function
- _ismbbalpha function
- _ismbbalpha_l function
ms.assetid: 8e54cb92-fc2b-41f5-8ab4-b22ac8aa9ad0
ms.openlocfilehash: 93ae26ff54af4cdee5f99e51c8f85d14ec51ae4e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335663"
---
# <a name="_ismbbalpha-_ismbbalpha_l"></a>_ismbbalpha, _ismbbalpha_l

지정된 멀티바이트 문자가 영문자인지 여부를 확인합니다.

## <a name="syntax"></a>구문

```C
int _ismbbalpha(
   unsigned int c
);
int _ismbbalpha_l(
   unsigned int c
);
```

### <a name="parameters"></a>매개 변수

*c*<br/>
테스트할 정수입니다.

*locale*<br/>
사용할 로캘입니다.

## <a name="return-value"></a>반환 값

식이 다음과 같이 0이 아닌 값을 반환 **_ismbbalpha**

`isalpha(c) || _ismbbkalnum(c)`

*c* 의 경우 0이 아니고, 그렇지 않으면 0입니다. **_ismbbalpha** 은 모든 로캘 종속 문자 설정에 대해 현재 로캘을 사용 합니다. **_ismbbalpha_l** 은 전달 된 로캘을 사용 한다는 점을 제외 하 고 동일 합니다.

## <a name="remarks"></a>설명

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](../global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**_ismbbalpha**|\<mbctype.h>|
|**_ismbbalpha_l**|\<mbctype.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="see-also"></a>참고 항목

[바이트 분류](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb 루틴](../../c-runtime-library/ismbb-routines.md)<br/>
