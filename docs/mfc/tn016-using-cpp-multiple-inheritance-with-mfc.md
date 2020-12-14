---
description: '자세히 알아보기: TN016: MFC에서 c + + 다중 상속 사용'
title: 'TN016: MFC에서 C++ 다중 상속 사용'
ms.date: 06/28/2018
f1_keywords:
- vc.inheritance
helpviewer_keywords:
- TN016
- MI (Multiple Inheritance)
- multiple inheritance, MFC support for
ms.assetid: 4ee27ae1-1410-43a5-b111-b6af9b84535d
ms.openlocfilehash: ac4b082a5dc33e93098453714acd25fbd0c18438
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215952"
---
# <a name="tn016-using-c-multiple-inheritance-with-mfc"></a>TN016: MFC에서 C++ 다중 상속 사용

이 정보에서는 Microsoft Foundation Classes에서 여러 상속 (MI)을 사용 하는 방법에 대해 설명 합니다. MFC에는 MI를 사용할 필요가 없습니다. MI는 MFC 클래스에서 사용 되지 않으며 클래스 라이브러리를 작성 하는 데 필요 하지 않습니다.

다음 하위 항목에서는 MI의 몇 가지 제한 사항에 대해 설명 하는 것 외에도 MI에서 일반적인 MFC 관용구 사용에 미치는 영향에 대해 설명 합니다. 이러한 제한 사항 중 일부는 일반적인 c + + 제한 사항입니다. 다른 항목은 MFC 아키텍처에 의해 적용 됩니다.

이 기술 정보를 마치면 MI를 사용 하는 완전 한 MFC 응용 프로그램을 찾을 수 있습니다.

## <a name="cruntimeclass"></a>CRuntimeClass

MFC의 지 속성 및 동적 개체 생성 메커니즘에서는 [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) 데이터 구조를 사용 하 여 클래스를 고유 하 게 식별 합니다. MFC는 이러한 구조체 중 하나를 응용 프로그램의 각 동적 및/또는 serialize 가능한 클래스와 연결 합니다. 이러한 구조체는 응용 프로그램을 시작할 때 형식의 특수 정적 개체를 사용 하 여 초기화 됩니다 `AFX_CLASSINIT` .

의 현재 구현은 `CRuntimeClass` MI 런타임 형식 정보를 지원 하지 않습니다. 이는 MFC 응용 프로그램에서 MI를 사용할 수 없다는 의미는 아닙니다. 그러나 둘 이상의 기본 클래스를 포함 하는 개체를 사용 하는 경우에는 특정 책임이 있습니다.

[CObject:: IsKindOf](../mfc/reference/cobject-class.md#iskindof) 메서드는 여러 기본 클래스가 있는 경우 개체의 형식을 올바르게 결정 하지 않습니다. 따라서 [cobject](../mfc/reference/cobject-class.md) 를 가상 기본 클래스로 사용할 수 없으며, `CObject` [cobject:: Serialize](../mfc/reference/cobject-class.md#serialize) 및 [cobject:: operator new](../mfc/reference/cobject-class.md#operator_new) 와 같은 멤버 함수에 대 한 모든 호출에는 c + +에서 적절 한 함수 호출을 구분할 수 있도록 범위 한정자가 있어야 합니다. 프로그램에서 MFC 내에 MI를 사용 하는 경우 기본 클래스를 포함 하는 클래스는 `CObject` 기본 클래스 목록에서 맨 왼쪽 클래스 여야 합니다.

대안은 연산자를 사용 하는 것입니다 **`dynamic_cast`** . MI를 사용 하 여 개체를 기본 클래스 중 하나로 캐스팅 하면 컴파일러가 제공 된 기본 클래스의 함수를 강제로 사용 합니다. 자세한 내용은 [Dynamic_cast 연산자](../cpp/dynamic-cast-operator.md)를 참조 하세요.

## <a name="cobject---the-root-of-all-classes"></a>CObject-모든 클래스의 루트

모든 중요 한 클래스는 클래스에서 직접 또는 간접적으로 파생 `CObject` 됩니다. `CObject` 에는 멤버 데이터가 없지만 일부 기본 기능이 있습니다. MI를 사용 하는 경우 일반적으로 두 개 이상의 파생 클래스에서 상속 됩니다 `CObject` . 다음 예제에서는 클래스를 [CFrameWnd](../mfc/reference/cframewnd-class.md) 및 [CObList](../mfc/reference/coblist-class.md)에서 상속할 수 있는 방법을 보여 줍니다.

```cpp
class CListWnd : public CFrameWnd, public CObList
{
    // ...
};
CListWnd myListWnd;
```

이 경우 `CObject` 는 두 번 포함 됩니다. 즉, 메서드 또는 연산자에 대 한 참조를 명확 하 게 구분 하는 방법이 필요 `CObject` 합니다. **Operator new** 및 [operator delete](../mfc/reference/cobject-class.md#operator_delete) 는 명확 하 게 구분 해야 하는 두 개의 연산자입니다. 또 다른 예로, 다음 코드는 컴파일 시간에 오류를 발생 시킵니다.

```cpp
myListWnd.Dump(afxDump); // compile time error, CFrameWnd::Dump or CObList::Dump
```

## <a name="reimplementing-cobject-methods"></a>Reimplementing CObject 메서드

두 개 이상의 파생 된 기본 클래스를 포함 하는 새 클래스를 만드는 경우 `CObject` 다른 사용자가 사용 하도록 할 메서드를 다시 구현 해야 합니다 `CObject` . 연산자 **`new`** 및 **`delete`** 는 필수 이며 [덤프](../mfc/reference/cobject-class.md#dump) 를 권장 합니다. 다음 예제에서는 **`new`** 및 **`delete`** 연산자와 메서드를 다시 구현 합니다 `Dump` .

```cpp
class CListWnd : public CFrameWnd, public CObList
{
public:
    void* operator new(size_t nSize)
    {
        return CFrameWnd:: operator new(nSize);
    }
    void operator delete(void* p)
    {
        CFrameWnd:: operator delete(p);
    }
    void Dump(CDumpContent& dc)
    {
        CFrameWnd::Dump(dc);
        CObList::Dump(dc);
    }
    // ...
};
```

## <a name="virtual-inheritance-of-cobject"></a>CObject의 가상 상속

거의 상속 하는 것이 함수 모호성 문제를 해결 하는 것 처럼 보일 수도 있지만 그렇지 않은 경우도 있습니다 `CObject` . 에는 멤버 데이터가 없으므로 `CObject` 기본 클래스 멤버 데이터의 여러 복사본을 방지 하기 위해 가상 상속이 필요 하지 않습니다. 이전에 표시 된 첫 번째 예제에서 `Dump` 가상 메서드는 및에서 다르게 구현 되기 때문에 여전히 모호 합니다 `CFrameWnd` `CObList` . 모호성을 제거 하는 가장 좋은 방법은 이전 섹션에 제공 된 권장 사항을 따르는 것입니다.

## <a name="cobjectiskindof-and-run-time-typing"></a>CObject:: IsKindOf 및 Run-Time 입력

에서 MFC가 지 원하는 런타임 입력 메커니즘은 `CObject` 매크로 DECLARE_DYNAMIC, IMPLEMENT_DYNAMIC, DECLARE_DYNCREATE, IMPLEMENT_DYNCREATE, DECLARE_SERIAL 및 IMPLEMENT_SERIAL를 사용 합니다. 이러한 매크로는 런타임 형식 검사를 수행 하 여 안전 다운 캐스트를 보장할 수 있습니다.

이러한 매크로는 단일 기본 클래스만 지원 하며 상속 된 클래스 곱하기에 대해 제한 된 방법으로 작동 합니다. IMPLEMENT_DYNAMIC 또는 IMPLEMENT_SERIAL에서 지정 하는 기본 클래스는 첫 번째 또는 가장 왼쪽의 기본 클래스 여야 합니다. 이 배치를 통해 가장 왼쪽에 있는 기본 클래스에 대 한 형식 검사를 수행할 수 있습니다. 런타임 형식 시스템에서는 추가 기본 클래스에 대해 알 수 없습니다. 다음 예제에서 런타임 시스템은에 대해 형식 검사 `CFrameWnd` 를 수행 하지만에 대해서는 아무 것도 알 수 없습니다 `CObList` .

```cpp
class CListWnd : public CFrameWnd, public CObList
{
    DECLARE_DYNAMIC(CListWnd)
    // ...
};
IMPLEMENT_DYNAMIC(CListWnd, CFrameWnd)
```

## <a name="cwnd-and-message-maps"></a>CWnd 및 메시지 맵

MFC 메시지 맵 시스템이 제대로 작동 하려면 다음과 같은 두 가지 추가 요구 사항이 있습니다.

- `CWnd`파생 된 기본 클래스는 하나만 있어야 합니다.

- `CWnd`-파생 된 기본 클래스는 첫 번째 또는 가장 왼쪽의 기본 클래스 여야 합니다.

다음은 작동 하지 않는 몇 가지 예입니다.

```cpp
class CTwoWindows : public CFrameWnd, public CEdit
{ /* ... */ }; // error : two copies of CWnd

class CListEdit : public CObList, public CEdit
{ /* ... */ }; // error : CEdit (derived from CWnd) must be first
```

## <a name="a-sample-program-using-mi"></a>MI를 사용 하는 샘플 프로그램

다음 샘플은 및 CWinApp에서 파생 된 클래스 하나를 구성 하는 독립 실행형 응용 프로그램입니다 `CFrameWnd` . [](../mfc/reference/cwinapp-class.md) 이러한 방식으로 응용 프로그램을 구성 하는 것은 좋지 않지만,이는 클래스가 하나 있는 가장 작은 MFC 응용 프로그램의 예입니다.

```cpp
#include <afxwin.h>

class CHelloAppAndFrame : public CFrameWnd, public CWinApp
{
public:
    CHelloAppAndFrame() {}

    // Necessary because of MI disambiguity
    void* operator new(size_t nSize)
        { return CFrameWnd::operator new(nSize); }
    void operator delete(void* p)
        { CFrameWnd::operator delete(p); }

    // Implementation
    // CWinApp overrides
    virtual BOOL InitInstance();
    // CFrameWnd overrides
    virtual void PostNcDestroy();
    afx_msg void OnPaint();

    DECLARE_MESSAGE_MAP()
};

BEGIN_MESSAGE_MAP(CHelloAppAndFrame, CFrameWnd)
    ON_WM_PAINT()
END_MESSAGE_MAP()

// because the frame window is not allocated on the heap, we must
// override PostNCDestroy not to delete the frame object
void CHelloAppAndFrame::PostNcDestroy()
{
    // do nothing (do not call base class)
}

void CHelloAppAndFrame::OnPaint()
{
    CPaintDC dc(this);
    CRect rect;
    GetClientRect(rect);

    CString s = "Hello, Windows!";
    dc.SetTextAlign(TA_BASELINE | TA_CENTER);
    dc.SetTextColor(::GetSysColor(COLOR_WINDOWTEXT));
    dc.SetBkMode(TRANSPARENT);
    dc.TextOut(rect.right / 2, rect.bottom / 2, s);
}

// Application initialization
BOOL CHelloAppAndFrame::InitInstance()
{
    // first create the main frame
    if (!CFrameWnd::Create(NULL, "Multiple Inheritance Sample",
        WS_OVERLAPPEDWINDOW, rectDefault))
        return FALSE;

    // the application object is also a frame window
    m_pMainWnd = this;
    ShowWindow(m_nCmdShow);
    return TRUE;
}

CHelloAppAndFrame theHelloAppAndFrame;
```

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
