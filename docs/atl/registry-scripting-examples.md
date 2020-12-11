---
description: '자세한 정보: 레지스트리 스크립팅 예제'
title: 레지스트리 스크립팅 예제
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
ms.openlocfilehash: 716aa69ed95c784079e72f9b785fedd8c07b0563
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157544"
---
# <a name="registry-scripting-examples"></a>레지스트리 스크립팅 예제

이 항목의 스크립팅 예제에서는 시스템 레지스트리에 키를 추가 하 고, 등록자 COM 서버를 등록 하 고, 여러 구문 분석 트리를 지정 하는 방법을 보여 줍니다.

## <a name="add-a-key-to-hkey_current_user"></a>HKEY_CURRENT_USER에 키 추가

다음 구문 분석 트리는 단일 키를 시스템 레지스트리에 추가 하는 간단한 스크립트를 보여 줍니다. 특히 스크립트는 키를에 추가 합니다 `MyVeryOwnKey` `HKEY_CURRENT_USER` . 또한의 기본 문자열 값을 `HowGoesIt` 새 키에 할당 합니다.

```rgs
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

이 스크립트는 다음과 같이 여러 하위 키를 정의 하도록 쉽게 확장할 수 있습니다.

```rgs
HKCU
{
    'MyVeryOwnKey' = s 'HowGoesIt'
    {
        'HasASubkey'
        {
            'PrettyCool' = d '55'
            val 'ANameValue' = s 'WithANamedValue'
        }
    }
}
```

이제 스크립트는 하위 키를에 추가 `HasASubkey` `MyVeryOwnKey` 합니다. 이 하위 키에는 `PrettyCool` 하위 키 (기본값 `DWORD` 55)와 `ANameValue` 명명 된 값 (문자열 값)이 모두 추가 `WithANamedValue` 됩니다.

## <a name="register-the-registrar-com-server"></a><a name="_atl_register_the_registrar_com_server"></a> 등록자 COM 서버 등록

다음 스크립트는 등록자 COM 서버 자체를 등록 합니다.

```rgs
HKCR
{
    ATL.Registrar = s 'ATL Registrar Class'
    {
        CLSID = s '{44EC053A-400F-11D0-9DCD-00A0C90391D3}'
    }
    NoRemove CLSID
    {
        ForceRemove {44EC053A-400F-11D0-9DCD-00A0C90391D3} = s 'ATL Registrar Class'
        {
            ProgID = s 'ATL.Registrar'
            InprocServer32 = s '%MODULE%'
            {
                val ThreadingModel = s 'Apartment'
            }
        }
    }
}
```

런타임에이 구문 분석 트리는 `ATL.Registrar` 키를에 추가 `HKEY_CLASSES_ROOT` 합니다. 새 키를 입력 하면 다음을 수행 합니다.

- `ATL Registrar Class`키의 기본 문자열 값으로를 지정 합니다.

- `CLSID`하위 키로를 추가 합니다.

- `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`에 대해를 지정 합니다 `CLSID` . 이 값은에 사용할 등록자의 CLSID입니다 `CoCreateInstance` .

`CLSID`는 공유 되므로 등록 취소 모드에서는 제거 하면 안 됩니다. 문은이를 `NoRemove CLSID` 수행 합니다 .이는를 `CLSID` 등록 모드에서 열고 등록 취소 모드에서 무시 해야 함을 나타냅니다.

`ForceRemove`문은 키를 다시 만들기 전에 키와 모든 하위 키를 제거 하 여 정리 함수를 제공 합니다. 이는 하위 키의 이름이 변경 된 경우에 유용할 수 있습니다. 이 스크립팅 예제에서는 `ForceRemove` 이미 존재 하는지 확인 `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` 합니다. 그렇지 않으면 다음을 `ForceRemove` 수행 합니다.

- `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`및 모든 하위 키를 재귀적으로 삭제 합니다.

- 을 다시 만듭니다 `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` .

- `ATL Registrar Class`에 대 한 기본 문자열 값으로를 추가 `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` 합니다.

이제 구문 분석 트리는에 두 개의 새 하위 키를 추가 `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` 합니다. 첫 번째 키인는 `ProgID` ProgID 인 기본 문자열 값을 가져옵니다. 두 번째 키인는 `InprocServer32` `%MODULE%` 이 문서의 [대체 가능 매개 변수 (등록자의 전처리기)를 사용 하 여](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)섹션에서 설명 하는 전처리기 값인 기본 문자열 값을 가져옵니다. `InprocServer32` 는 문자열 값이 인 명명 된 값도 가져옵니다 `ThreadingModel` `Apartment` .

## <a name="specify-multiple-parse-trees"></a>여러 구문 분석 트리 지정

스크립트에서 두 개 이상의 구문 분석 트리를 지정 하려면 다른 트리 끝에 하나의 트리를 추가 하기만 하면 됩니다. 예를 들어 다음 스크립트는 `MyVeryOwnKey` 및에 대 한 구문 분석 트리에 키를 추가 합니다 `HKEY_CLASSES_ROOT` `HKEY_CURRENT_USER` .

```rgs
HKCR
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

> [!NOTE]
> 등록자 스크립트에서 4K는 최대 토큰 크기입니다. 토큰은 구문에서 인식할 수 있는 모든 요소입니다. 이전 스크립팅 예제에서,, `HKCR` `HKEY_CURRENT_USER` `'MyVeryOwnKey'` 및 `'HowGoesIt'` 는 모두 토큰입니다.

## <a name="see-also"></a>참고 항목

[등록자 스크립트 만들기](../atl/creating-registrar-scripts.md)
