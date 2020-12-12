---
description: '자세한 정보: MFC 소스 파일 사용'
title: MFC 소스 파일 사용
ms.date: 08/19/2019
helpviewer_keywords:
- public members
- source files
- MFC, source files
- MFC source files
- comments, MFC
- private member access
- protected member access
- source files, MFC
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
ms.openlocfilehash: 42dc285bf4877c4bef70e430b6d2982f43e08d51
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143262"
---
# <a name="using-the-mfc-source-files"></a>MFC 소스 파일 사용

MFC(Microsoft Foundation Class) 라이브러리는 전체 소스 코드를 제공합니다. 헤더 파일 (.h)은 *\atlmfc\include* 디렉터리에 있습니다. 구현 파일 (.cpp)은 *\atlmfc\src\mfc* 디렉터리에 있습니다.

이 문서에서는 MFC에서 각 클래스의 다양 한 부분을 설명 하는 데 사용 하는 규칙, 이러한 주석의 의미, 각 섹션에서 찾을 수 있는 것을 설명 합니다. Visual Studio 마법사는 사용자를 위해 만든 클래스에 대해 비슷한 규칙을 사용 하며, 이러한 규칙은 사용자의 코드에 유용 합니다.

**`public`**, **`protected`** 및 **`private`** c + + 키워드에 대해 잘 알고 있을 수 있습니다. MFC 헤더 파일에는 각 클래스에 여러 개의 클래스가 있을 수 있습니다. 예를 들어 public 멤버 변수 및 함수는 둘 이상의 키워드 아래에 있을 수 있습니다 **`public`** . MFC는 허용 되는 액세스 형식이 아니라 사용에 따라 멤버 변수와 함수를 분리 하기 때문입니다. MFC는 **`private`** 경우에만 사용 됩니다. 구현 세부 정보로 간주 되는 항목에도 **`protected`** 많은 시간이 **`public`** 있습니다. 구현 세부 사항에 직접 액세스하는 것은 권장되지 않지만 MFC는 이런 결정을 개발자의 몫으로 남겨둡니다.

MFC 응용 프로그램 마법사가 생성한 MFC 소스 파일 및 헤더 파일 양쪽 모두 클래스 선언부 안에서 다음과 같은 주석을 확인할 수 있습니다. (보통 다음의 순서대로 나타납니다.)

`// Constructors`

`// Attributes`

`// Operations`

`// Overridables`

`// Implementation`

## <a name="an-example-of-the-comments"></a><a name="an-example-of-the-comments"></a> 주석의 예

클래스의 다음 부분 목록은 MFC에서 클래스를 사용 하 여 `CStdioFile` 클래스 멤버를 사용 하는 방식으로 나누는 표준 주석을 대부분 사용 합니다.

```cpp
/*============================================================================*/
// STDIO file implementation

class CStdioFile : public CFile
{
    DECLARE_DYNAMIC(CStdioFile)

public:
// Constructors
    CStdioFile();

    // . . .

// Attributes
    FILE* m_pStream;    // stdio FILE
                        // m_hFile from base class is _fileno(m_pStream)

// Operations
    // reading and writing strings
    virtual void WriteString(LPCTSTR lpsz);
    virtual LPTSTR ReadString(_Out_writes_z_(nMax) LPTSTR lpsz, _In_ UINT nMax);
    virtual BOOL ReadString(CString& rString);

// Implementation
public:
    virtual ~CStdioFile();
#ifdef _DEBUG
    void Dump(CDumpContext& dc) const;
#endif
    virtual ULONGLONG GetPosition() const;
    virtual ULONGLONG GetLength() const;
    virtual BOOL Open(LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL);

    // . . .

protected:
    void CommonBaseInit(FILE* pOpenStream, CAtlTransactionManager* pTM);
    void CommonInit(LPCTSTR lpszFileName, UINT nOpenFlags, CAtlTransactionManager* pTM);
};
```

이러한 주석은 비슷한 종류의 클래스 멤버를 포함하는 클래스 선언의 섹션을 일관되게 표시합니다. 규칙을 설정 하는 것이 아니라 MFC 규칙 이라는 점에 유의 하세요.

## <a name="-constructors-comment"></a>생성자 주석

`// Constructors`MFC 클래스 선언의 섹션에는 생성자 (c + +의 의미) 및 개체를 사용 하는 데 필요한 모든 초기화 함수가 선언 됩니다. 예를 들어 `CWnd` 객체를 사용하기 전에 먼저 C++ 생성자를 호출한 다음 `Create` 함수를 호출하여 "완전히 생성"해야 하므로 `CWnd::Create`는 생성자 섹션에 있습니다. 일반적으로 이러한 멤버는 공용입니다.

예를 들어 클래스에는 `CStdioFile` 5 개의 생성자가 있으며, 그 중 하나는 [주석의 예제](#an-example-of-the-comments)아래 목록에 표시 됩니다.

## <a name="-attributes-comment"></a>특성 주석

MFC 클래스 선언의 `// Attributes` 섹션은 개체의 공용 특성(또는 속성)을 포함합니다. 일반적으로 특성은 멤버 변수 또는 Get/Set 함수입니다. "Get"이나 "Set" 함수는 가상일 수도 있고 아닐 수도 있습니다. "Get" 함수는 대부분의 **`const`** 경우 의도 하지 않은 결과가 발생 하지 않기 때문에 종종 발생 합니다. 이러한 멤버는 일반적으로 공개입니다. Protected 및 private 특성은 일반적으로 구현 섹션에서 찾을 수 있습니다.

클래스의 샘플 목록에서 `CStdioFile` [주석의 예](#an-example-of-the-comments)아래에는 *m_pStream* 멤버 변수 하나가 포함 되어 있습니다. `CDC` 클래스에는 이 주석에서 약 20개의 멤버가 있습니다.

> [!NOTE]
> `CDC`나 `CWnd`와 같은 큰 클래스에는 너무 많은 멤버가 있어 한 그룹에 모든 속성을 단순히 나열하면 명확하지 못할 수 있습니다. 이러한 경우 클래스 라이브러리는 다른 주석을 제목으로 사용하여 멤버에 대하여 상세히 설명합니다. 예를 들어 `CDC`는 `// Device-Context Functions`, `// Drawing Tool Functions`, `// Drawing Attribute Functions` 등을 사용합니다. 특성을 나타내는 그룹은 위에 설명된 일반적인 구문을 따릅니다. 많은 OLE 클래스에는 `// Interface Maps`라는 구현 섹션이 있습니다.

## <a name="-operations-comment"></a>작업 주석

`// Operations`MFC 클래스 선언의 섹션에는 개체에 대해 호출 하 여 작업을 수행 하거나 작업을 수행 (작업 수행) 할 수 있는 멤버 함수가 포함 되어 있습니다. 일반적으로 이러한 함수는 의도 하지 않은 결과를 발생 하므로 일반적이 지 않습니다 **`const`** . 클래스의 필요에 따라 가상 또는 비가상이 될 수 있습니다. 일반적으로 이러한 멤버는 공용입니다.

클래스의 샘플 목록에서 `CStdioFile` [주석의 예](#an-example-of-the-comments)에서는이 주석 아래에 세 개의 멤버 함수 `WriteString` 및의 두 오버 로드를 포함 `ReadString` 합니다.

특성과 마찬가지로 작업을 더 세분화할 수 있습니다.

## <a name="-overridables-comment"></a>재정의 가능 주석

MFC 클래스 선언의 `// Overridables` 섹션에는 기본 클래스 동작을 수정해야 할 때 파생 클래스에서 재정의할 수있는 가상 함수가 포함되어 있습니다. 일반적으로 "설정"으로 이름이 지정 되지만 반드시 필요한 것은 아닙니다. 여기의 함수는 재정의할 수 있도록 설계되었으며 종종 일종의 "callback" 또는 "hook"를 구현하거나 제공합니다. 일반적으로 이러한 멤버는 protected입니다.

MFC 자체 내에서, 순수 가상 함수는 항상 이 섹션에 배치됩니다. C + +의 순수 가상 함수는 다음 형식을 사용 합니다.

`virtual void OnDraw( ) = 0;`

클래스의 샘플 목록에서 `CStdioFile` [주석의 예](#an-example-of-the-comments)에서는 목록에 재정의 가능 섹션이 포함 되어 있지 않습니다. 반면 `CDocument` 클래스에는 약 10개의 재정의 가능한 멤버 함수가 나열되어 있습니다.

일부 클래스에서는 `// Advanced Overridables`라는 주석이 표시될 수도 있습니다. 이러한 함수는 고급 프로그래머만 재정의 하려고 하는 함수입니다. 이를 재정의할 필요는 없습니다.

> [!NOTE]
> 이 문서에서 설명하는 규칙은 일반적으로 자동화(이전의 OLE 자동화) 방법 및 속성에 대해서도 잘 작동합니다. 자동화 방법은 MFC 작업과 비슷합니다. 자동화 속성은 MFC 특성과 비슷합니다. 자동화 이벤트(이전의 OLE 컨트롤로 알려진 ActiveX 컨트롤에 대한 지원)는 MFC 재정의 가능한 멤버 함수와 유사합니다.

## <a name="-implementation-comment"></a>구현 주석

`// Implementation` 섹션은 모든 MFC 클래스 선언에서 가장 중요한 부분입니다.

이 섹션에는 모든 구현 세부 정보가 포함됩니다. 멤버 변수 및 멤버 함수가 이 섹션에 포함되어 있습니다. 이 줄 아래 모든 항목은 이후 릴리스의 MFC에서 변경될 수 있습니다. 이를 방지할 수 없는 한 줄 아래의 세부 정보를 사용 하면 안 `// Implementation` 됩니다. 또한 구현 줄 아래에 선언 된 멤버는 문서화 되지 않지만 일부 구현은 기술 참고 자료에 설명 되어 있습니다. 기본 클래스의 가상 함수 재정의는 기본 클래스 함수가 정의 된 섹션과 상관 없이이 섹션에 있습니다. 함수가 기본 클래스 구현을 재정의 하는 경우 구현 세부 정보로 간주 됩니다. 일반적으로 이러한 멤버는 protected이지만 항상 그렇지는 않습니다.

주석 `CStdioFile` [예제](#an-example-of-the-comments)아래에 있는 목록에서 주석 아래에 선언 된 멤버를 `// Implementation` , 또는로 선언할 수 **`public`** 있습니다 **`protected`** **`private`** . 이러한 멤버는 나중에 변경 될 수 있으므로 주의 해 서 사용 해야 합니다. **`public`** 클래스 라이브러리 구현이 제대로 작동 하려면 멤버 그룹을로 선언 해야 할 수 있습니다. 그러나 선언 된 멤버를 안전 하 게 사용할 수 있다는 의미는 아닙니다.

> [!NOTE]
> `// Implementation` 주석의 위 또는 아래에 나머지 형식의 주석이 있을 수 있습니다. 두 경우 모두 아래에 선언된 멤버의 종류를 설명합니다. `// Implementation` 주석 이후에 나타나는 경우, 향후 버전의 MFC에서 멤버가 변경될 수 있음을 가정해야 합니다.

## <a name="see-also"></a>참고 항목

[일반 MFC 항목](../mfc/general-mfc-topics.md)
