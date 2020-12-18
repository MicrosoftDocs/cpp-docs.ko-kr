---
description: '자세한 정보: MFC 확장 DLL'
title: 확장명 DLL
ms.date: 05/06/2019
helpviewer_keywords:
- memory [C++], DLLs
- MFC extension DLLs [C++]
- AFXDLL library
- shared resources [C++]
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- resource sharing [C++]
- extension DLLs [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: f69ac3d4-e474-4b1c-87a1-6738843a135c
ms.openlocfilehash: 6500d8ba3cfcc4311ef993064aa9516f27fa45d6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156478"
---
# <a name="mfc-extension-dlls"></a>MFC 확장 DLL

MFC 확장 DLL은 일반적으로 기존 MFC 라이브러리 클래스에서 파생된 다시 사용할 수 있는 클래스를 구현하는 DLL입니다.

MFC 확장 DLL의 특징과 요구 사항은 다음과 같습니다.

- 클라이언트 실행 파일은 `_AFXDLL`을 정의하여 컴파일된 MFC 애플리케이션이어야 합니다.

- MFC 확장 DLL은 MFC에 동적으로 연결된 기본 MFC DLL에서도 사용할 수 있습니다.

- MFC 확장 DLL은 `_AFXEXT`를 정의하여 컴파일해야 합니다. 이렇게 해야 `_AFXDLL`도 정의되고 MFC 헤더 파일에서 적절한 선언을 가져옵니다. 또한 DLL을 빌드하는 동안 `AFX_EXT_CLASS`를 `__declspec(dllexport)`로 정의해야 하며, MFC 확장 DLL에서 이 매크로를 사용하여 클래스를 선택하는 경우 이 DLL이 필요합니다.

- MFC 확장 DLL은 `CWinApp`에서 파생된 클래스를 인스턴스화하지 않아야 하지만, 클라이언트 애플리케이션(또는 DLL)을 사용하여 이 개체를 제공해야 합니다.

- 그러나 MFC 확장 DLL은 `DllMain` 함수를 제공하고 이 함수에서 필요한 초기화를 수행해야 합니다.

확장 DLL은 MFC의 동적 연결 라이브러리 버전(MFC의 공유 버전이라고도 함)을 사용하여 빌드됩니다. 공유 버전의 MFC로 빌드된 MFC 실행 파일(애플리케이션 또는 기본 MFC DLL)만 MFC 확장 DLL을 사용할 수 있습니다. 클라이언트 애플리케이션과 MFC 확장 DLL은 모두 동일한 버전의 MFCx0.dll을 사용해야 합니다. MFC 확장 DLL을 사용하면 MFC에서 새로운 사용자 지정 클래스를 파생한 다음 이 확장 버전의 MFC를 DLL을 호출하는 애플리케이션에 제공할 수 있습니다.

MFC에서 파생된 개체를 애플리케이션과 DLL 간에 전달하는 데에도 확장 DLL을 사용할 수 있습니다. 전달된 개체와 연결된 멤버 함수는 개체가 생성된 모듈에 있습니다. MFC의 공유 DLL 버전을 사용할 때 관련 함수를 제대로 내보내므로 MFC 또는 MFC 파생 개체 포인터는 애플리케이션과 애플리케이션에서 로드하는 MFC 확장 DLL 간에 자유롭게 전달할 수 있습니다.

MFC 확장 DLL은 애플리케이션에서 MFC의 공유 DLL 버전을 사용하는 것과 동일한 방식으로 공유 버전의 MFC를 사용하지만, 몇 가지 사항을 추가로 고려해야 합니다.

- `CWinApp` 파생 개체가 없습니다. 클라이언트 애플리케이션의 `CWinApp` 파생 개체를 사용해야 합니다. 따라서 클라이언트 애플리케이션이 기본 메시지 펌프, 유휴 루프 등을 소유합니다.

- `DllMain` 함수에서 `AfxInitExtensionModule`를 호출합니다. 이 함수의 반환 값을 확인해야 합니다. `AfxInitExtensionModule`에서 0 값을 반환하는 경우 `DllMain` 함수에서 0값을 반환합니다.

- MFC 확장 DLL이 애플리케이션으로 `CRuntimeClass` 개체 또는 리소스를 내보내려는 경우 초기화하는 동안 **CDynLinkLibrary** 개체를 만듭니다.

MFC 버전 4.0 이전에는 이 형식의 DLL을 AFXDLL이라고 했습니다. AFXDLL은 DLL을 빌드할 때 정의된 `_AFXDLL` 전처리기 기호를 나타냅니다.

MFC 공유 버전의 가져오기 라이브러리는 [MFC DLL의 명명 규칙](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)에 설명된 규칙에 따라 이름이 지정됩니다. Visual Studio에서는 미리 빌드된 버전의 MFC DLL과 함께 애플리케이션에서 사용하고 배포할 수 있는 여러 비 MFC DLL을 제공합니다. 관련 내용은 Program Files\Microsoft Visual Studio 폴더에 설치되는 Redist .txt에 설명되어 있습니다.

.def 파일을 사용하여 내보내는 경우 헤더 파일의 시작과 끝에 다음 코드를 추가합니다.

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

네 줄을 추가하면 MFC 확장 DLL에 맞게 코드가 올바르게 컴파일됩니다. 이 네 줄을 생략하면 DLL이 잘못 컴파일되거나 연결될 수 있습니다.

MFC 또는 MFC 파생 개체 포인터를 MFC DLL 간에 전달해야 하는 경우 DLL은 MFC 확장 DLL이어야 합니다. 전달된 개체와 연결된 멤버 함수는 개체가 생성된 모듈에 있습니다. MFC의 공유 DLL 버전을 사용할 때 관련 함수를 제대로 내보내므로 MFC 또는 MFC 파생 개체 포인터는 애플리케이션과 애플리케이션에서 로드하는 MFC 확장 DLL 간에 자유롭게 전달할 수 있습니다.

C++ 이름 꾸미기 및 내보내기 문제로 인해 MFC 확장 DLL의 내보내기 목록이 동일한 DLL의 디버그 및 정품 버전과 다른 플랫폼의 DLL 간에 다를 수 있습니다. 정품 MFCx0.dll에는 약 2,000개의 내보낸 진입점이 있고, 디버그 MFCx0D.dll에는 약 3,000개의 내보낸 진입점이 있습니다.

## <a name="memory-management"></a>메모리 관리

클라이언트 애플리케이션의 주소 공간에 로드된 MFCx0.dll 및 모든 MFC 확장 DLL은 같은 애플리케이션에 있는 것처럼 동일한 메모리 할당자, 리소스 로드 및 기타 MFC 전역 상태를 사용합니다. 이것이 중요한 이유는 비 MFC DLL 라이브러리와 기본 MFC DLL은 정확히 반대로 자체 메모리 풀에서 각 DLL에 메모리를 할당하기 때문입니다.

MFC 확장 DLL에서 메모리를 할당하는 경우 해당 메모리는 애플리케이션에서 할당된 다른 개체와 자유롭게 혼합할 수 있습니다. 또한 동적으로 MFC에 연결하는 애플리케이션이 실패하는 경우 운영 체제의 보호 기능을 통해 DLL을 공유하는 다른 모든 MFC 애플리케이션의 무결성을 유지합니다.

마찬가지로 리소스를 로드할 현재 실행 파일과 같은 다른 전역 MFC 상태도 클라이언트 애플리케이션과 모든 MFC 확장 DLL 및 MFCx0.dll 자체 간에 공유됩니다.

## <a name="sharing-resources-and-classes"></a>리소스 및 클래스 공유

리소스 내보내기는 리소스 목록을 통해 수행됩니다. 각 애플리케이션에는 **CDynLinkLibrary** 개체의 단일 연결된 목록이 포함되어 있습니다. 리소스를 찾을 때 리소스를 로드하는 표준 MFC 구현 대부분은 먼저 현재 리소스 모듈(`AfxGetResourceHandle`)을 찾고 리소스를 찾을 수 없는 경우 **CDynLinkLibrary** 개체 목록을 검색하여 요청된 리소스를 로드하려고 합니다.

목록 검색은 약간 느리고 리소스 ID 범위를 관리해야 한다는 단점이 있습니다. 여러 MFC 확장 DLL에 연결하는 클라이언트 애플리케이션이 DLL 인스턴스 핸들을 지정하지 않고도 모든 DLL 제공 리소스를 사용할 수 있다는 장점도 있습니다. `AfxFindResourceHandle`은 리소스 목록을 검색하여 지정된 일치 항목을 찾는 데 사용되는 API입니다. 이 API는 리소스의 이름 및 형식을 사용하고 처음 발견된 리소스 핸들(또는 NULL)을 반환합니다.

목록을 검색하지 않고 특정 위치의 리소스만 로드하려면 `AfxGetResourceHandle` 및 `AfxSetResourceHandle` 함수를 사용하여 이전 핸들을 저장하고 새 핸들을 설정합니다. 클라이언트 애플리케이션으로 돌아가기 전에 이전 리소스 핸들을 복원해야 합니다. 이 방법을 사용하여 메뉴를 명시적으로 로드하는 예제는 MFC 샘플 [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)에서 Testdll2 .cpp를 참조하세요.

MFC 이름을 지정하고 MFC 개체를 동적으로 만드는 것도 유사합니다. MFC 개체 deserialization 메커니즘에서는 이전에 저장된 항목을 기반으로 필요한 형식의 C++ 개체를 동적으로 만들어 다시 생성할 수 있도록 모든 `CRuntimeClass` 개체를 등록해야 합니다.

MFC 샘플 [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)의 경우 목록은 다음과 같습니다.

```
head ->   DLLHUSK.EXE   - or -   DLLHUSK.EXE
               |                      |
          TESTDLL2.DLL           TESTDLL2.DLL
               |                      |
          TESTDLL1.DLL           TESTDLL1.DLL
               |                      |
           MFCOxxD.DLL                |
               |                      |
           MFCDxxD.DLL                |
               |                      |
            MFCxxD.DLL            MFCxx.DLL
```

여기서 *xx* 는 버전 번호입니다. 예를 들어 42는 버전 4.2를 나타냅니다.

MFCxx.dll은 일반적으로 리소스 및 클래스 목록의 마지막에 있습니다. Mfcxx.dll에는 모든 표준 명령 ID의 프롬프트 문자열을 비롯해 모든 표준 MFC 리소스가 포함되어 있습니다. 이 파일을 목록의 끝에 배치하여 DLL 및 클라이언트 애플리케이션에서 표준 MFC 리소스의 자체 복사본을 포함하지 않고 대신 Mfcxx.dll의 공유 리소스를 사용할 수 있습니다.

모든 DLL의 리소스 및 클래스 이름을 클라이언트 애플리케이션의 이름 공간에 병합하는 경우 ID나 이름을 선택할 때 주의해야 한다는 단점이 있습니다.

[DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk) 샘플에서는 여러 헤더 파일을 사용하여 공유 리소스 이름 공간을 관리합니다.

MFC 확장 DLL이 각 애플리케이션의 추가 데이터를 유지 관리해야 하는 경우 **CDynLinkLibrary** 에서 새 클래스를 파생하고 `DllMain`에서 만들 수 있습니다. DLL은 실행될 때 현재 애플리케이션의 **CDynLinkLibrary** 개체 목록을 확인하여 해당하는 특정 MFC 확장 DLL의 개체를 찾을 수 있습니다.

### <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [MFC 확장 DLL 초기화](run-time-library-behavior.md#initializing-extension-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [공유 리소스 파일 사용 팁](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)

- [MFC의 DLL 버전](../mfc/tn033-dll-version-of-mfc.md)

- [정적으로 MFC에 연결된 기본 MFC DLL](regular-dlls-statically-linked-to-mfc.md)

- [동적으로 MFC에 연결된 기본 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [기본 MFC DLL에서 데이터베이스, OLE 및 소켓 MFC 확장명 DLL 사용](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

## <a name="see-also"></a>참조

[Visual Studio에서 C/C++ DLL 만들기](dlls-in-visual-cpp.md)
