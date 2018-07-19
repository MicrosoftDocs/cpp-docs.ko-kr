---
title: 레지스트리 스크립트 예제 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c192e8bec1d32dd7d7a7953e5da72a139c7520e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361891"
---
# <a name="registry-scripting-examples"></a>레지스트리 스크립팅 예제
이 항목의 스크립팅 예제에는 시스템 레지스트리에 키를 추가, 등록자 COM 서버를 등록 합니다. 여러 구문 분석 트리를 지정 하는 방법을 보여 줍니다.  
  
## <a name="add-a-key-to-hkeycurrentuser"></a>HKEY_CURRENT_USER에 키 추가  
 다음 구문 분석 트리 시스템 레지스트리에 단일 키를 추가 하는 간단한 스크립트를 보여 줍니다. 스크립트에서 키를 추가 하 고 특히 `MyVeryOwnKey`을 `HKEY_CURRENT_USER`입니다. 기본 문자열 값으로 할당 `HowGoesIt` 에서 새 키:  
  
```  
HKEY_CURRENT_USER  
{  
 'MyVeryOwnKey' = s 'HowGoesIt'  
}  
```  
  
 이 스크립트 여러 하위 키를 다음과 같이 정의를 쉽게 확장할 수 있습니다.  
  
```  
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
  
 스크립트에 하위 키를 추가 하 고 이제 `HasASubkey`을 `MyVeryOwnKey`입니다. 이 하위 키를 추가 둘 다는 `PrettyCool` 하위 키 (기본값 `DWORD` 55의 값) 및 `ANameValue` 명명 된 값 (의 문자열 값을 가진 `WithANamedValue`).  
  
##  <a name="_atl_register_the_registrar_com_server"></a> 등록 기관 COM 서버를 등록 합니다.  
 다음 스크립트는 등록자 COM 서버 자체를 등록합니다.  
  
```  
HKCR  
{  
    ATL.Registrar = s 'ATL Registrar Class'  
 {  
    CLSID = s '{44EC053A-400F-11D0-9DCD-00A0C90391D3}'  
 }  
    NoRemove CLSID  
 {  
    ForceRemove {44EC053A-400F-11D0-9DCD-00A0C90391D3} = 
    s 'ATL Registrar Class'  
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
  
 이 구문 분석 트리, 런타임에 추가 `ATL.Registrar` 키를 `HKEY_CLASSES_ROOT`합니다. 이 새 키에 다음 it:  
  
-   지정 `ATL Registrar Class` 키의 기본 문자열 값으로.  
  
-   추가 `CLSID` 하위 키로 합니다.  
  
-   지정 `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` 에 대 한 `CLSID`합니다. (이 값은 등록자의 CLSID와 함께 사용할 `CoCreateInstance`.)  
  
 이후 `CLSID` 가, 이전에 공유 것을 제거할 수 없음 등록 취소 모드에서. 문, `NoRemove CLSID`를 지정 하 여이 작업을 수행 `CLSID` 레지스터 모드로 연 등록 취소 모드에서는 무시 해야 합니다.  
  
 `ForceRemove` 문은 키 다시 만들기 전에 키와 모든 하위 키를 제거 하 여 하우스키핑 함수를 제공 합니다. 이 하위 키의 이름을 변경 된 경우에 유용할 수 있습니다. 이 예에서 스크립팅 `ForceRemove` 확인 하 `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` 이미 있습니다. 그렇지 않으면 `ForceRemove`:  
  
-   재귀적으로 삭제 `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` 및 모든 하위 키입니다.  
  
-   다시 생성 `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`합니다.  
  
-   추가 `ATL Registrar Class` 에 대 한 기본 문자열 값으로 `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`합니다.  
  
 구문 분석 트리를 두 개의 새 하위 키를 지금 추가 `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`합니다. 첫 번째 키 `ProgID`, ProgID는 기본 문자열 값을 가져옵니다. 두 번째 키 `InprocServer32`, 기본 문자열 값을 가져옵니다 `%MODULE%`, 즉 섹션에 설명 된 전처리기 값 [를 사용 하 여 대체 가능 매개 변수 (The 등록자 전처리기)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md),이 문서의. `InprocServer32` 또한 명명된 된 값을 가져옵니다 `ThreadingModel`의 문자열 값을 가진 `Apartment`합니다.  
  
## <a name="specify-multiple-parse-trees"></a>여러 구문 분석 트리를 지정 합니다.  
 스크립트에서 둘 이상의 구문 분석 트리를 지정 하려면 다른의 끝에 트리를 배치 합니다. 다음 스크립트는 키를 추가 하는 예를 들어 `MyVeryOwnKey`, 둘 다에 대해 구문 분석 트리를 `HKEY_CLASSES_ROOT` 및 `HKEY_CURRENT_USER`:  
  
```  
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
>  등록자 스크립트에서 4k는 최대 토큰 크기입니다. (토큰 구문에서 인식할 수 있는 모든 요소입니다.) 이전 스크립팅 예에서 `HKCR`, `HKEY_CURRENT_USER`, `'MyVeryOwnKey'`, 및 `'HowGoesIt'` 은 모든 토큰.  
  
## <a name="see-also"></a>참고 항목  
 [등록자 스크립트 만들기](../atl/creating-registrar-scripts.md)

