---
description: '자세한 정보: Cmfc리본 Applicationbutton 클래스'
title: Cmfc리본 Applicationbutton 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::SetImage
helpviewer_keywords:
- CMFCRibbonApplicationButton [MFC], CMFCRibbonApplicationButton
- CMFCRibbonApplicationButton [MFC], SetImage
ms.assetid: beb81757-fabd-4641-9130-876ba8505b78
ms.openlocfilehash: 391274c7540e7e52a19c20e17a09b25f37badcd6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289805"
---
# <a name="cmfcribbonapplicationbutton-class"></a>Cmfc리본 Applicationbutton 클래스

애플리케이션 창의 왼쪽 위 모서리에 있는 특수 단추를 구현합니다. 클릭하면 단추는 **열기** , **저장** 및 **종료** 와 같은 일반적인 **파일** 명령이 포함된 메뉴를 엽니다.

## <a name="syntax"></a>구문

```
class CMFCRibbonApplicationButton : public CMFCRibbonButton
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[Cmfc리본 Applicationbutton:: Cmfc리본 Applicationbutton](#cmfcribbonapplicationbutton)|`CMFCRibbonApplicationButton` 개체를 생성하고 초기화합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|`CMFCRibbonApplicationButton::CreateObject`|프레임워크에서 이 클래스 형식의 동적 인스턴스를 만드는 데 사용합니다.|
|`CMFCRibbonApplicationButton::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|[Cmfc리본 Applicationbutton:: SetImage](#setimage)|리본 응용 프로그램 단추에 이미지를 할당 합니다.|

## <a name="example"></a>예제

다음 예제에서는 `CMFCRibbonApplicationButton` 클래스에서 다양한 메서드를 사용하는 방법을 보여 줍니다. 예제에서는 응용 프로그램 단추에 이미지를 할당 하는 방법 및 도구 설명을 설정 하는 방법을 보여 줍니다. 이 코드 조각은 [클라이언트 그리기 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_DrawClient#4](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_1.h)]
[!code-cpp[NVC_MFC_DrawClient#5](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxribbonbar.h

## <a name="cmfcribbonapplicationbuttoncmfcribbonapplicationbutton"></a><a name="cmfcribbonapplicationbutton"></a> Cmfc리본 Applicationbutton:: Cmfc리본 Applicationbutton

[Cmfc리본 Applicationbutton](../../mfc/reference/cmfcribbonapplicationbutton-class.md) 개체를 생성 하 고 초기화 합니다.

```
CMFCRibbonApplicationButton();
CMFCRibbonApplicationButton(UINT uiBmpResID);
CMFCRibbonApplicationButton(HBITMAP hBmp);
```

### <a name="parameters"></a>매개 변수

*uiBmpResID*<br/>
응용 프로그램 단추에 표시할 이미지의 리소스 ID입니다.

*hBmp*<br/>
응용 프로그램 단추에 표시 되는 비트맵에 대 한 핸들입니다.

### <a name="remarks"></a>설명

리본 응용 프로그램 단추는 응용 프로그램 창의 왼쪽 위 모퉁이에 있는 특수 단추입니다. 사용자가이 단추를 클릭 하면 응용 프로그램에서 **열기**, **저장** 및 **종료** 와 같은 일반적인 **파일** 명령이 포함 된 메뉴를 엽니다.

## <a name="cmfcribbonapplicationbuttonsetimage"></a><a name="setimage"></a> Cmfc리본 Applicationbutton:: SetImage

응용 프로그램 단추에 이미지를 할당 합니다.

```cpp
void SetImage(UINT uiBmpResID);
void SetImage(HBITMAP hBmp);
```

### <a name="parameters"></a>매개 변수

*uiBmpResID*<br/>
진행 응용 프로그램 단추에 표시할 이미지의 리소스 ID입니다.

*hBmp*<br/>
진행 응용 프로그램 단추에 표시 되는 비트맵에 대 한 핸들입니다.

### <a name="remarks"></a>설명

단추를 만든 후이 메서드를 사용 하 여 리본 응용 프로그램 단추에 새 이미지를 할당 합니다. 응용 프로그램 단추는 응용 프로그램 창의 왼쪽 위 모퉁이에 있습니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[Cmfc리본 단추 클래스](../../mfc/reference/cmfcribbonbutton-class.md)
