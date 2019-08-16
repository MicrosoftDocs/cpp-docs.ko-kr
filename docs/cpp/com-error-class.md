---
title: _com_error 클래스
ms.date: 11/04/2016
f1_keywords:
- _com_error
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
ms.openlocfilehash: 828a1ec68fef631700d5b64e6aeeec6660acf9a8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498741"
---
# <a name="_com_error-class"></a>_com_error 클래스

**Microsoft 전용**

**_Com_error** 개체는 형식 라이브러리 또는 com 지원 클래스 중 하나에서 생성 된 헤더 파일의 오류 처리 래퍼 함수에 의해 검색 된 예외 상태를 나타냅니다. **_Com_error** 클래스는 HRESULT 오류 코드 및 관련 된 `IErrorInfo Interface` 모든 개체를 캡슐화 합니다.

### <a name="construction"></a>구성

|||
|-|-|
|[_com_error](../cpp/com-error-com-error.md)|**_Com_error** 개체를 생성 합니다.|

### <a name="operators"></a>연산자

|||
|-|-|
|[operator =](../cpp/com-error-operator-equal.md)|기존 **_com_error** 개체를 다른 개체에 할당 합니다.|

### <a name="extractor-functions"></a>추출기 함수

|||
|-|-|
|[오류](../cpp/com-error-error.md)|생성자에 전달 된 HRESULT를 검색 합니다.|
|[ErrorInfo](../cpp/com-error-errorinfo.md)|생성자에 `IErrorInfo` 전달 된 개체를 검색 합니다.|
|[WCode](../cpp/com-error-wcode.md)|캡슐화 된 HRESULT에 매핑된 16 비트 오류 코드를 검색 합니다.|

### <a name="ierrorinfo-functions"></a>IErrorInfo 함수

|||
|-|-|
|[설명](../cpp/com-error-description.md)|함수 `IErrorInfo::GetDescription` 를 호출 합니다.|
|[HelpContext](../cpp/com-error-helpcontext.md)|함수 `IErrorInfo::GetHelpContext` 를 호출 합니다.|
|[HelpFile](../cpp/com-error-helpfile.md)|Calls `IErrorInfo::GetHelpFile` 함수|
|[원본](../cpp/com-error-source.md)|함수 `IErrorInfo::GetSource` 를 호출 합니다.|
|[GUID](../cpp/com-error-guid.md)|함수 `IErrorInfo::GetGUID` 를 호출 합니다.|

### <a name="format-message-extractor"></a>메시지 추출기 서식 지정

|||
|-|-|
|[ErrorMessage](../cpp/com-error-errormessage.md)|**_Com_error** 개체에 저장 된 HRESULT에 대 한 문자열 메시지를 검색 합니다.|

### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo ... HRESULT 매퍼

|||
|-|-|
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|32 비트 HRESULT를 16 비트 `wCode`에 매핑합니다.|
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|16 비트 `wCode` 를 32 비트 HRESULT에 매핑합니다.|

**Microsoft 전용 종료**

## <a name="requirements"></a>요구 사항

**헤더:** \<comdef >

`Lib:`comsuppw 또는 compw. lib (자세한 내용은 [/zc: wchar_t (Wchar_t Is Native Type)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 참조)

## <a name="see-also"></a>참고자료

[컴파일러 COM 지원 클래스](../cpp/compiler-com-support-classes.md)<br/>
[IErrorInfo 인터페이스](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)