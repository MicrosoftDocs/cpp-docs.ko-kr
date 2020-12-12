---
description: '다음에 대 한 자세한 정보: AFX_EXTENSION_MODULE 구조체'
title: AFX_EXTENSION_MODULE 구조체
ms.date: 11/04/2016
f1_keywords:
- AFX_EXTENSION_MODULE
helpviewer_keywords:
- AFX_EXTENSION_MODULE structure [MFC]
ms.assetid: b85a989c-d0c5-4b28-b53c-dad45b75704e
ms.openlocfilehash: d3a5abd449f13a06aa5d7388b2dd2926a6011973
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248231"
---
# <a name="afx_extension_module-structure"></a>AFX_EXTENSION_MODULE 구조체

는 mfc 확장명 `AFX_EXTENSION_MODULE` dll 모듈의 상태를 유지 하기 위해 mfc 확장명 dll을 초기화 하는 동안 사용 됩니다.

## <a name="syntax"></a>구문

```
struct AFX_EXTENSION_MODULE
{
    BOOL bInitialized;
    HMODULE hModule;
    HMODULE hResource;
    CRuntimeClass* pFirstSharedClass;
    COleObjectFactory* pFirstSharedFactory;
};
```

#### <a name="parameters"></a>매개 변수

*bInitialized 됨*<br/>
DLL 모듈이를 사용 하 여 초기화 되었으면 TRUE `AfxInitExtensionModule` 입니다.

*hModule*<br/>
DLL 모듈의 핸들을 지정 합니다.

*hResource*<br/>
DLL 사용자 지정 리소스 모듈의 핸들을 지정 합니다.

*pFirstSharedClass*<br/>
`CRuntimeClass`DLL 모듈의 첫 번째 런타임 클래스에 대 한 정보 (구조)에 대 한 포인터입니다. 런타임 클래스 목록의 시작을 제공 하는 데 사용 됩니다.

*pFirstSharedFactory*<br/>
DLL 모듈의 첫 번째 개체 팩터리 (개체)에 대 한 포인터 `COleObjectFactory` 입니다. 클래스 팩터리 목록의 시작을 제공 하는 데 사용 됩니다.

## <a name="remarks"></a>설명

MFC 확장 Dll은 함수에서 다음 두 가지 작업을 수행 해야 합니다 `DllMain` .

- [AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule) 을 호출 하 고 반환 값을 확인 합니다.

- DLL이 `CDynLinkLibrary` [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체를 내보내거나 고유한 사용자 지정 리소스를 포함 하는 경우 개체를 만듭니다.

`AFX_EXTENSION_MODULE`구조체는를 입력 하기 전에 실행 되는 일반 정적 개체 생성의 일부로 mfc 확장 dll에 의해 초기화 된 런타임 클래스 개체의 복사본을 포함 하 여 mfc 확장 dll 모듈 상태의 복사본을 보관 하는 데 사용 됩니다 `DllMain` . 예를 들어:

[!code-cpp[NVC_MFC_DLL#2](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_1.cpp)]

구조에 저장 된 모듈 정보를 `AFX_EXTENSION_MODULE` 개체에 복사할 수 있습니다 `CDynLinkLibrary` . 예를 들어:

[!code-cpp[NVC_MFC_DLL#5](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_2.cpp)]

## <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="see-also"></a>참고 항목

[구조체, 스타일, 콜백 및 메시지 맵](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule)<br/>
[AfxTermExtensionModule](extension-dll-macros.md#afxtermextensionmodule)
