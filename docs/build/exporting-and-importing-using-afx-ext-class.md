---
description: '자세한 정보: AFX_EXT_CLASS를 사용하여 내보내기 및 가져오기'
title: AFX_EXT_CLASS를 사용하여 내보내기 및 가져오기
ms.date: 11/04/2016
f1_keywords:
- afx_ext_class
helpviewer_keywords:
- AFX_EXT_CLASS macro
- exporting classes [C++]
- importing DLLs [C++]
- extension DLLs [C++], exporting classes
- executable files [C++], importing classes
- exporting DLLs [C++], AFX_EXT_CLASS macro
ms.assetid: 6b72cb2b-e92e-4ecd-bcab-c335e1d1cfde
ms.openlocfilehash: 9c82874b1e5e8791f2825cf6874399fab0e10eaa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156686"
---
# <a name="exporting-and-importing-using-afx_ext_class"></a>AFX_EXT_CLASS를 사용하여 내보내기 및 가져오기

[MFC 확장 DLL](extension-dlls-overview.md)은 **AFX_EXT_CLASS** 매크로를 사용하여 클래스를 내보냅니다. MFC 확장 DLL에 연결되는 실행 파일은 이 매크로를 사용하여 클래스를 가져옵니다. **AFX_EXT_CLASS** 매크로를 사용하여 MFC 확장 DLL을 빌드하는 데 사용되는 헤더 파일을 DLL로 연결되는 실행 파일과 함께 사용할 수 있습니다.

DLL에 대한 헤더 파일에서 다음과 같이 **AFX_EXT_CLASS** 키워드를 클래스 선언에 추가합니다.

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

이 매크로는 전처리기 기호 `_AFXDLL` 및 `_AFXEXT`가 정의되는 경우 MFC에 의해 `__declspec(dllexport)`로 정의됩니다. 그러나 `_AFXDLL`이 정의되고 `_AFXEXT`가 정의되지 않은 경우에는 이 매크로는 `__declspec(dllimport)`로 정의됩니다. 전처리기 기호 `_AFXDLL`이 정의된 경우 이는 MFC의 공유 버전이 대상 실행 파일(DLL 또는 애플리케이션)에서 사용되고 있음을 나타냅니다. `_AFXDLL` 및 `_AFXEXT`가 모두 정의된 경우 이는 대상 실행 파일이 MFC 확장 DLL임을 나타냅니다.

`AFX_EXT_CLASS`는 MFC 확장 DLL에서 내보낼 때 `__declspec(dllexport)`로 정의되므로 .def 파일에서 해당 클래스의 모든 기호에 대한 데코레이팅된 이름을 넣지 않고도 전체 클래스를 내보낼 수 있습니다.

이 방법을 사용하여 .def 파일 및 클래스에 대한 모든 데코레이팅된 이름을 만들지 않을 수 있지만 .def 파일을 만들면 서수를 사용하여 이름을 내보낼 수 있으므로 더 효율적입니다. 내보내기 방법으로 .def 파일을 사용하려면 헤더 파일의 시작과 끝에 다음 코드를 추가합니다.

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

> [!CAUTION]
> 인라인 함수를 내보낼 때는 버전 충돌이 발생할 수 있기 때문에 주의해야 합니다. 인라인 함수는 애플리케이션 코드로 확장됩니다. 따라서 나중에 함수를 다시 작성하는 경우 애플리케이션 자체를 다시 컴파일하지 않는 한 함수는 업데이트되지 않습니다. 일반적으로 DLL 함수는 이 함수를 사용하는 애플리케이션을 다시 빌드하지 않고도 업데이트할 수 있습니다.

## <a name="exporting-individual-members-in-a-class"></a>클래스에서 개별 멤버 내보내기

때로는 클래스의 개별 멤버를 내보내야 할 수 있습니다. 예를 들어 `CDialog` 파생 클래스를 내보내는 경우 생성자와 `DoModal` 호출만 내보내야 할 수 있습니다. 내보내야 하는 개별 멤버에 `AFX_EXT_CLASS`를 사용할 수 있습니다.

예를 들어:

```cpp
class CExampleDialog : public CDialog
{
public:
   AFX_EXT_CLASS CExampleDialog();
   AFX_EXT_CLASS int DoModal();
   ...
   // rest of class definition
   ...
};
```

더 이상 클래스의 모든 멤버를 내보내지 않으므로 MFC 매크로 작동 방식 때문에 추가 문제가 발생할 수 있습니다. 여러 MFC 도우미 매크로는 실제로 데이터 멤버를 선언하거나 정의합니다. 따라서 이러한 데이터 멤버도 DLL에서 내보내야 합니다.

예를 들어 `DECLARE_DYNAMIC` 매크로는 MFC 확장 DLL을 빌드할 때 다음과 같이 정의됩니다.

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
   static CRuntimeClass* PASCAL _GetBaseClass(); \
public: \
   static AFX_DATA CRuntimeClass class##class_name; \
   virtual CRuntimeClass* GetRuntimeClass() const; \
```

정적 `AFX_DATA`로 시작하는 줄은 클래스 내부에서 정적 개체를 선언하는 것입니다. 이 클래스를 올바르게 내보내고 클라이언트 실행 파일의 런타임 정보에 액세스하려면 이 정적 개체를 내보내야 합니다. 정적 개체는 한정자 `AFX_DATA`를 사용하여 선언되므로 `AFX_DATA`를 DLL을 빌드할 때 `__declspec(dllexport)`로 정의하고 클라이언트 실행 파일을 빌드할 때 `__declspec(dllimport)`로 정의하면 됩니다. 이러한 방식으로 `AFX_EXT_CLASS`가 이미 정의되어 있기 때문에 클래스 정의 주위에서 `AFX_DATA`를 `AFX_EXT_CLASS`와 동일하게 재정의해야 합니다.

예를 들어:

```cpp
#undef  AFX_DATA
#define AFX_DATA AFX_EXT_CLASS

class CExampleView : public CView
{
   DECLARE_DYNAMIC()
   // ... class definition ...
};

#undef  AFX_DATA
#define AFX_DATA
```

MFC는 매크로 내에서 정의하는 데이터 항목에 대해 항상 `AFX_DATA` 기호를 사용하기 때문에 이 기술은 이러한 모든 시나리오에서 유효합니다. 예를 들어 `DECLARE_MESSAGE_MAP`에 대해 작동합니다.

> [!NOTE]
> 클래스의 일부 멤버가 아니라 전체 클래스를 내보내는 경우 정적 데이터 멤버가 자동으로 내보내집니다.

### <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [.def 파일을 사용하여 DLL에서 내보내기](exporting-from-a-dll-using-def-files.md)

- [__declspec(dllexport)을 사용하여 DLL에서 내보내기](exporting-from-a-dll-using-declspec-dllexport.md)

- [C 언어 실행 파일에서 사용할 C++ 함수 내보내기](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [C 또는 C++ 언어 실행 파일에서 사용할 C 함수 내보내기](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [사용할 내보내기 방법 결정](determining-which-exporting-method-to-use.md)

- [__declspec(dllimport)을 사용하여 애플리케이션으로 가져오기](importing-into-an-application-using-declspec-dllimport.md)

- [DLL 초기화](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [데코레이팅된 이름](reference/decorated-names.md)

- [인라인 함수 가져오기 및 내보내기](importing-and-exporting-inline-functions.md)

- [상호 가져오기](mutual-imports.md)

## <a name="see-also"></a>참조

[DLL에서 내보내기](exporting-from-a-dll.md)
