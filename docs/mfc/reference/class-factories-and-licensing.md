---
description: '자세히 알아보기: 클래스 팩터리 및 라이선스'
title: 클래스 팩터리 및 라이선스
ms.date: 11/04/2016
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
ms.openlocfilehash: 7470a5828df358a28db5a30832f98314e09a133e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236843"
---
# <a name="class-factories-and-licensing"></a>클래스 팩터리 및 라이선스

OLE 컨트롤의 인스턴스를 만들기 위해 컨테이너 응용 프로그램은 컨트롤의 클래스 팩터리의 멤버 함수를 호출 합니다. 컨트롤이 실제 OLE 개체 이기 때문에 클래스 팩터리는 컨트롤의 인스턴스를 만드는 역할을 담당 합니다. 모든 OLE 컨트롤 클래스에는 클래스 팩터리가 있어야 합니다.

OLE 컨트롤의 또 다른 중요 한 기능은 라이선스를 적용 하는 기능입니다. ControlWizard를 사용 하면 컨트롤 프로젝트를 만드는 동안 라이선스를 통합할 수 있습니다. 컨트롤 라이선스에 대 한 자세한 내용은 [Activex 컨트롤: Activex 컨트롤 라이선스](../../mfc/mfc-activex-controls-licensing-an-activex-control.md)문서를 참조 하세요.

다음 표에서는 컨트롤의 클래스 팩터리 및 컨트롤의 라이선스를 선언 하 고 구현 하는 데 사용 되는 여러 매크로와 함수를 보여 줍니다.

### <a name="class-factories-and-licensing"></a>클래스 팩터리 및 라이선스

|매크로 또는 함수|설명|
|-|-|
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|OLE 컨트롤이 나 속성 페이지에 대 한 클래스 팩터리를 선언 합니다.|
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|컨트롤의 함수를 구현 `GetClassID` 하 고 클래스 팩터리의 인스턴스를 선언 합니다.|
|[BEGIN_OLEFACTORY](#begin_olefactory)|라이선스 함수의 선언을 시작 합니다.|
|[END_OLEFACTORY](#end_olefactory)|라이선스 함수의 선언을 종료 합니다.|
|[AfxVerifyLicFile](#afxverifylicfile)|특정 컴퓨터에서 사용이 허가 된 컨트롤 인지 여부를 확인 합니다.|

## <a name="declare_olecreate_ex"></a><a name="declare_olecreate_ex"></a> DECLARE_OLECREATE_EX

클래스 팩터리와 `GetClassID` 컨트롤 클래스의 멤버 함수를 선언 합니다.

```
DECLARE_OLECREATE_EX(class_name)
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
컨트롤 클래스의 이름입니다.

### <a name="remarks"></a>설명

라이선스를 지원 하지 않는 컨트롤에 대해 컨트롤 클래스 헤더 파일에서이 매크로를 사용 합니다.

이 매크로는 다음 코드 샘플과 동일한 용도로 사용 됩니다.

[!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]

### <a name="requirements"></a>요구 사항

  **헤더** afxctl

## <a name="implement_olecreate_ex"></a><a name="implement_olecreate_ex"></a> IMPLEMENT_OLECREATE_EX

컨트롤 클래스의 클래스 팩터리와 [Getclassid](../../mfc/reference/colecontrol-class.md#getclassid) 멤버 함수를 구현 합니다.

```
IMPLEMENT_OLECREATE_EX(
   class_name,
    external_name,
    l,
    w1,
    w2,
    b1,
    b2,
    b3,
    b4,
    b5,
    b6,
    b7,
    b8)
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
컨트롤 속성 페이지 클래스의 이름입니다.

*external_name*<br/>
응용 프로그램에 노출 되는 개체 이름입니다.

*l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8*<br/>
클래스 CLSID의 구성 요소입니다. 이러한 매개 변수에 대 한 자세한 내용은 [IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate)에 대 한 설명을 참조 하십시오.

### <a name="remarks"></a>설명

이 매크로는 DECLARE_OLECREATE_EX 매크로 또는 BEGIN_OLEFACTORY 및 END_OLEFACTORY 매크로를 사용 하는 모든 컨트롤 클래스의 구현 파일에 표시 되어야 합니다. 외부 이름은 다른 응용 프로그램에 노출 되는 OLE 컨트롤의 식별자입니다. 컨테이너는이 이름을 사용 하 여이 컨트롤 클래스의 개체를 요청 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxctl

## <a name="begin_olefactory"></a><a name="begin_olefactory"></a> BEGIN_OLEFACTORY

컨트롤 클래스의 헤더 파일에서 클래스 팩터리의 선언을 시작 합니다.

```
BEGIN_OLEFACTORY(class_name)
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
클래스 팩터리를 포함 하는 컨트롤 클래스의 이름을 지정 합니다.

### <a name="remarks"></a>설명

클래스 팩터리 라이선스 함수의 선언은 BEGIN_OLEFACTORY 직후에 시작 해야 합니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxctl

## <a name="end_olefactory"></a><a name="end_olefactory"></a> END_OLEFACTORY

컨트롤의 클래스 팩터리 선언을 끝냅니다.

```
END_OLEFACTORY(class_name)
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
클래스 팩터리가 있는 컨트롤 클래스의 이름입니다.

### <a name="requirements"></a>요구 사항

  **헤더** afxctl

## <a name="afxverifylicfile"></a><a name="afxverifylicfile"></a> AfxVerifyLicFile

로 명명 된 라이선스 파일이 `pszLicFileName` OLE 컨트롤에 대해 유효한 지 확인 하려면이 함수를 호출 합니다.

```
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,
    LPCTSTR  pszLicFileName,
    LPOLESTR  pszLicFileContents,
    UINT cch = -1);
```

### <a name="parameters"></a>매개 변수

*hInstance*<br/>
사용이 허가 된 컨트롤과 연결 된 DLL의 인스턴스 핸들입니다.

*pszLicFileName*<br/>
라이선스 파일 이름을 포함 하는 null로 끝나는 문자열을 가리킵니다.

*pszLicFileContents*<br/>
라이선스 파일의 시작 부분에 있는 시퀀스와 일치 해야 하는 바이트 시퀀스를 가리킵니다.

*cch*<br/>
*PszLicFileContents* 의 문자 수입니다.

### <a name="return-value"></a>반환 값

라이선스 파일이 있고 *pszLicFileContents* 에서 문자 시퀀스로 시작 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*Cch* 가-1 인 경우이 함수는 다음을 사용 합니다.

[!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]

### <a name="requirements"></a>요구 사항

  **헤더** afxctl

## <a name="see-also"></a>참고 항목

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)
