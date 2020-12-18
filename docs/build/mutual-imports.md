---
description: '자세한 정보: 상호 가져오기'
title: 상호 가져오기
ms.date: 11/04/2016
helpviewer_keywords:
- mutual DLL imports [C++]
- AFX_DATA
- importing DLLs [C++], mutual imports
- mutually importing executable files [C++]
- AFX_EXT_CLASS macro
- circular imports
- _AFXEXT preprocessor symbol
- DLLs [C++], importing
- executable files [C++], importing
- extension DLLs [C++], mutual imports
- exporting DLLs [C++], mutual imports
ms.assetid: 2cc29537-92ee-4d92-af39-8b8b3afd808f
ms.openlocfilehash: 0015dfe69237ff46ecfbef9ee1f1649fcb04d689
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187496"
---
# <a name="mutual-imports"></a>상호 가져오기

상호(또는 순환) 가져오기일 경우 다른 실행 파일로 내보내거나 가져오면 일이 복잡해집니다. 예를 들어 두 DLL은 상호 재귀 함수와 유사하게 서로 기호를 가져옵니다.

실행 파일(일반적으로 DLL)을 상호 가져올 때의 문제는 둘 다 다른 파일을 빌드하지 않고는 빌드할 수 없다는 것입니다. 각 빌드 프로세스에서는 다른 빌드 프로세스에서 생성한 가져오기 라이브러리를 입력으로 사용해야 합니다.

솔루션은 LIB 유틸리티에 /DEF 옵션을 사용하여 실행 파일을 빌드하지 않고 가져오기 라이브러리를 생성하는 것입니다. 이 유틸리티를 사용하면 관련 DLL의 수가 얼마나 많은지나 종속성이 얼마나 복잡한지와 상관없이 필요한 가져오기 라이브러리를 모두 빌드할 수 있습니다.

상호 가져오기를 처리하는 일반적인 솔루션은 다음과 같습니다.

1. 각 DLL을 차례로 가져옵니다. (어느 순서든 가능하지만 일부 순서가 더 적합합니다.) 필요한 가져오기 라이브러리가 모두 있고 최신이면 LINK를 실행하여 실행 파일(DLL)을 빌드합니다. 그러면 가져오기 라이브러리가 생성됩니다. 그러지 않으면 LIB를 실행하여 가져오기 라이브러리를 생성합니다.

   LIB를 /DEF 옵션과 함께 실행하면 .EXP 확장명의 추가 파일이 생성됩니다. .EXP 파일은 나중에 실행 파일을 빌드하는 데 사용해야 합니다.

1. LINK 또는 LIB를 사용하여 가져오기 라이브러리를 모두 빌드한 후 돌아가서 LINK를 실행하여 이전 단계에서 빌드되지 않은 모든 실행 파일을 빌드합니다. 해당 .exp 파일은 LINK 줄에 지정해야 합니다.

   이전에 LIB 유틸리티를 실행하여 DLL1의 가져오기 라이브러리를 생성한 경우 LIB에서는 DLL1.exp 파일도 생성했을 것입니다. DLL1.dlll을 빌드할 때 DLL1.exp를 LINK에 입력으로 사용해야 합니다.

다음 그림에서는 DLL1과 DLL2의 두 개 상호 가져오기 DLL을 위한 솔루션을 보여 줍니다. 1단계는 DLL1에서/DEF 옵션을 설정하고 LIB를 실행하는 것입니다. 1단계에서는 가져오기 라이브러리 DLL1.lib와 DLL1.exp를 생성합니다. 2단계에서는 가져오기 라이브러리를 사용하여 DLL2를 빌드합니다. 그러면 DLL2 기호의 가져오기 라이브러리가 생성됩니다. 3단계에서는 DLL1.exp와 DLL2.lib를 입력으로 사용하여 DLL1을 빌드합니다. DLL2의 가져오기 라이브러리를 빌드하기 위해 LIB를 사용하지 않았으므로 DLL2의 .exp 파일은 필요하지 않습니다.

![상호 가져오기를 사용하여 두 개의 DLL 연결](media/vc37yj1.gif "상호 가져오기를 사용하여 두 개의 DLL 연결")<br/>
상호 가져오기를 사용하여 두 개의 DLL 연결

## <a name="limitations-of-_afxext"></a>_AFXEXT의 제한 사항

MFC 확장 DLL의 여러 계층이 없는 경우 MFC 확장 DLL에 `_AFXEXT` 전처리기 기호를 사용할 수 있습니다. MFC 클래스에서 파생되는 고유한 MFC 확장 DLL의 클래스를 호출하거나 해당 클래스에서 파생되는 MFC 확장 DLL이 있는 경우 모호성을 방지하기 위해 고유한 전처리기 기호를 사용해야 합니다.

문제는 Win32에서 데이터를 DLL에서 내보내는 경우에는 명시적으로 **`__declspec(dllexport)`** 을 선언하고, 데이터를 DLL에서 가져오는 경우에는 명시적으로 **`__declspec(dllimport)`** 을 선언해야 한다는 것입니다. `_AFXEXT`를 정의할 때 MFC 헤더에서 **AFX_EXT_CLASS** 를 올바로 정의해야 합니다.

여러 계층이 있는 경우 **AFX_EXT_CLASS** 와 같은 하나의 기호로는 부족합니다. 왜냐하면 MFC 확장 DLL은 새 클래스를 내보낼 뿐 아니라 다른 MFC 확장 DLL에서 다른 클래스를 가져올 수도 있기 때문입니다. 이 문제를 해결하려면 DLL 자체를 빌드하고 있거나 DLL을 사용하고 있음을 나타내는 특수 전처리기 기호를 사용합니다. 예를 들어 두 개의 MFC 확장 DLL A.dll과 B.dll이 있다고 가정합니다. 두 DLL은 각각 A.h 및 B.h의 일부 클래스를 내보냅니다. B.dll은 A.dll의 클래스를 사용합니다. 헤더 파일은 다음과 같습니다.

```
/* A.H */
#ifdef A_IMPL
   #define CLASS_DECL_A   __declspec(dllexport)
#else
   #define CLASS_DECL_A   __declspec(dllimport)
#endif

class CLASS_DECL_A CExampleA : public CObject
{ ... class definition ... };

// B.H
#ifdef B_IMPL
   #define CLASS_DECL_B   __declspec(dllexport)
#else
   #define CLASS_DECL_B   __declspec(dllimport)
#endif

class CLASS_DECL_B CExampleB : public CExampleA
{ ... class definition ... };
...
```

A.dll은 빌드될 때 `/D A_IMPL`을 사용하여 빌드되고 B.dll은 `/D B_IMPL`을 사용하여 빌드됩니다. 각 DLL에 별도의 기호를 사용하면 B.dll을 빌드할 때 `CExampleB`를 내보내고 `CExampleA`를 가져옵니다. `CExampleA`는 A.dll을 빌드할 때 내보내고 B.dll(또는 다른 클라이언트)에서 사용될 때 가져옵니다.

이 유형의 계층화는 기본 제공 **AFX_EXT_CLASS** 및 `_AFXEXT` 전처리기 기호를 사용해서는 수행할 수 없습니다. 위에서 설명한 방법은 MFC 자체에서 활성 기술, 데이터베이스 및 네트워크 MFC 확장 DLL을 빌드할 때 사용하는 메커니즘과 다르지 않은 방식으로 이 문제를 해결합니다.

## <a name="not-exporting-the-entire-class"></a>전체 클래스를 내보내지 않음

전체 클래스를 내보내지 않는 경우 MFC 매크로에서 만든 필수 데이터 항목을 올바로 내보내야 합니다. 이 작업은 `AFX_DATA`를 특정 클래스의 매크로로 다시 정의하여 수행할 수 있습니다. 전체 클래스를 내보내지 않는 경우에는 항상 이 작업을 수행해야 합니다.

예를 들어:

```
/* A.H */
#ifdef A_IMPL
   #define CLASS_DECL_A  _declspec(dllexport)
#else
   #define CLASS_DECL_A  _declspec(dllimport)
#endif

#undef  AFX_DATA
#define AFX_DATA CLASS_DECL_A

class CExampleA : public CObject
{
   DECLARE_DYNAMIC()
   CLASS_DECL_A int SomeFunction();
   //... class definition ...
};

#undef AFX_DATA
#define AFX_DATA
```

### <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [DLL에서 내보내기](exporting-from-a-dll.md)

- [.DEF 파일을 사용하여 DLL에서 내보내기](exporting-from-a-dll-using-def-files.md)

- [__declspec(dllexport)을 사용하여 DLL에서 내보내기](exporting-from-a-dll-using-declspec-dllexport.md)

- [AFX_EXT_CLASS를 사용하여 내보내기 및 가져오기](exporting-and-importing-using-afx-ext-class.md)

- [C 언어 실행 파일에서 사용할 C++ 함수 내보내기](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [사용할 내보내기 방법 결정](determining-which-exporting-method-to-use.md)

- [__declspec(dllimport)을 사용하여 애플리케이션으로 가져오기](importing-into-an-application-using-declspec-dllimport.md)

### <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [LIB 유틸리티 및 /DEF 옵션](reference/lib-reference.md)

## <a name="see-also"></a>참조

[가져오기 및 내보내기](importing-and-exporting.md)
