---
description: '자세한 정보: 스크립트 호출'
title: 스크립트 호출 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- StringRegister method
- scripts, invoking registry in ATL
ms.assetid: eabd41ee-586b-4266-9e92-5aaad04b73a4
ms.openlocfilehash: 48fc49118d93893b5cd60462fbaecfdb73d747c3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152661"
---
# <a name="invoking-scripts"></a>스크립트 호출

대체 [가능 매개 변수 (등록 기관의 전처리기)를 사용 하 여](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) 대체 맵에 대해 설명 하 고 등록자 메서드 **addreplacement** 을 언급 합니다. 등록자는 스크립트와 관련 된 8 가지 다른 메서드를 포함 하며 모두 다음 표에 설명 되어 있습니다.

|메서드|구문/설명|
|------------|-------------------------|
|**ResourceRegister**|**HRESULT ResourceRegister (lpcolestr***resfilename* **, UINT** `nID` **, lpcolestr** `szType` **);**      <br /><br /> 모듈의 리소스에 포함 된 스크립트를 등록 합니다. *Resfilename* 은 모듈 자체에 대 한 UNC 경로를 나타냅니다. *nID* 및 *sztype* 에는 각각 리소스의 ID와 형식이 포함 됩니다.|
|**ResourceUnregister 취소**|**HRESULT resourceunregister 취소 (lpcolestr***resfilename* **, UINT** `nID` **, lpcolestr** `szType` **);**      <br /><br /> 모듈의 리소스에 포함 된 스크립트의 등록을 취소 합니다. *Resfilename* 은 모듈 자체에 대 한 UNC 경로를 나타냅니다. *nID* 및 *sztype* 에는 각각 리소스의 ID와 형식이 포함 됩니다.|
|**ResourceRegisterSz**|**HRESULT ResourceRegisterSz (lpcolestr***resfilename* **, lpcolestr***szid* **, lpcolestr** `szType` **);**      <br /><br /> 모듈의 리소스에 포함 된 스크립트를 등록 합니다. *Resfilename* 은 모듈 자체에 대 한 UNC 경로를 나타냅니다. *Szid* 및 *szid* 에는 각각 리소스의 문자열 식별자와 형식이 포함 됩니다.|
|**ResourceUnregisterSz**|**HRESULT ResourceUnregisterSz (LPCOLESTR** 을 위한 *파일 이름* **, lpcolestr***szid* **, lpcolestr** `szType` **);**      <br /><br /> 모듈의 리소스에 포함 된 스크립트의 등록을 취소 합니다. *Resfilename* 은 모듈 자체에 대 한 UNC 경로를 나타냅니다. *Szid* 및 *szid* 에는 각각 리소스의 문자열 식별자와 형식이 포함 됩니다.|
|**FileRegister**|**HRESULT FileRegister (LPCOLESTR**  *fileName*  **);**<br /><br /> 파일에 스크립트를 등록 합니다. *fileName* 은 리소스 스크립트를 포함 하거나 포함 하는 파일에 대 한 UNC 경로입니다.|
|**FileUnregister 취소**|**HRESULT FileUnregister 취소 (LPCOLESTR**  *fileName*  **);**<br /><br /> 파일에서 스크립트의 등록을 취소 합니다. *fileName* 은 리소스 스크립트를 포함 하거나 포함 하는 파일에 대 한 UNC 경로입니다.|
|**StringRegister**|**HRESULT StringRegister (LPCOLESTR**  *데이터*  **);**<br /><br /> 스크립트를 문자열에 등록 합니다. *데이터* 는 스크립트 자체를 포함 합니다.|
|**StringUnregister 취소**|**HRESULT StringUnregister 취소 (LPCOLESTR**  *데이터*  **);**<br /><br /> 문자열에서 스크립트의 등록을 취소 합니다. *데이터* 는 스크립트 자체를 포함 합니다.|

**ResourceRegisterSz** 및 **Resourceunregistersz** 는 **ResourceRegister 및 resource** 와 유사 하지만 문자열 식별자를 지정할 수 있습니다.

**FileRegister** 및 **fileunregister 취소** 메서드는 리소스의 스크립트를 원하지 않거나 자체 파일에 스크립트를 원하는 경우에 유용 합니다. **Stringregister** 및 **stringregister** 메서드를 사용 하 여 .rgs 파일을 동적으로 할당 된 문자열에 저장할 수 있습니다.

## <a name="see-also"></a>참고 항목

[등록자 스크립트 만들기](../atl/creating-registrar-scripts.md)
