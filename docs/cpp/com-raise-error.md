---
description: '다음에 대 한 자세한 정보: _com_raise_error'
title: _com_raise_error
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
ms.openlocfilehash: 81697b565104971d22da04a7b8b0e33a7f9255ac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178214"
---
# <a name="_com_raise_error"></a>_com_raise_error

**Microsoft 전용**

실패에 대 한 응답으로 [_com_error](../cpp/com-error-class.md) 을 throw 합니다.

## <a name="syntax"></a>구문

```cpp
void __stdcall _com_raise_error(
   HRESULT hr,
   IErrorInfo* perrinfo = 0
);
```

#### <a name="parameters"></a>매개 변수

*시간*<br/>
HRESULT 정보입니다.

*perrinfo*<br/>
`IErrorInfo` 개체입니다.

## <a name="remarks"></a>설명

에 정의 된 **_com_raise_error** 는 \<comdef.h> 동일한 이름 및 프로토타입의 사용자 작성 버전으로 바꿀 수 있습니다. 이는 `#import`를 사용하고 C++ 예외 처리는 사용하지 않으려는 경우 실행할 수 있습니다. 이 경우 **_com_raise_error** 사용자 버전은를 수행 `longjmp` 하거나 메시지 상자를 표시 하 고 중지 하도록 결정할 수 있습니다. 컴파일러 COM 지원 코드가 반환을 예상하고 있지 않기 때문에 사용자 버전은 반환할 수 없습니다.

[_Set_com_error_handler](../cpp/set-com-error-handler.md) 를 사용 하 여 기본 오류 처리 함수를 대체할 수도 있습니다.

기본적으로 **_com_raise_error** 는 다음과 같이 정의 됩니다.

```cpp
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {
   throw _com_error(hr, perrinfo);
}
```

**Microsoft 전용 종료**

## <a name="requirements"></a>요구 사항

**헤더:**\<comdef.h>

**Lib:** **Wchar_t 네이티브 형식** 컴파일러 옵션을 on으로 설정 하는 경우 comsuppw 또는 compw를 사용 합니다. **네이티브 형식이 off wchar_t** comsupp.lib를 사용 합니다. 자세한 내용은 [/zc: wchar_t (Wchar_t 네이티브 형식)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[컴파일러 COM 전역 함수](../cpp/compiler-com-global-functions.md)<br/>
[_set_com_error_handler](../cpp/set-com-error-handler.md)
