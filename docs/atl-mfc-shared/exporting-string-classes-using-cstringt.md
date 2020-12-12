---
description: '자세한 정보: CStringT를 사용 하 여 문자열 클래스 내보내기'
title: CStringT를 사용 하 여 문자열 클래스 내보내기
ms.date: 11/04/2016
helpviewer_keywords:
- CStringT class, exporting strings
ms.assetid: bdfc441e-8d2a-461c-9885-46178066c09f
ms.openlocfilehash: 8876ea04f1252e4f5861a950b04dabcd99d6a804
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166995"
---
# <a name="exporting-string-classes-using-cstringt"></a>CStringT를 사용 하 여 문자열 클래스 내보내기

이전에는 MFC 개발자가에서를 파생 `CString` 하 여 자체 문자열 클래스를 특수화 했습니다. Microsoft Visual C++ .NET (MFC 8.0)에서 [CString](../atl-mfc-shared/using-cstring.md) 클래스는 [CStringT](../atl-mfc-shared/reference/cstringt-class.md)라는 템플릿 클래스로 대체 되었습니다. 이는 다음과 같은 여러 가지 이점을 제공 합니다.

- MFC `CString` 클래스는 더 큰 mfc 정적 라이브러리나 DLL에서 연결 하지 않고도 ATL 프로젝트에서 사용할 수 있습니다.

- 새 템플릿 클래스를 사용 하 여 `CStringT` `CString` c + + 표준 라이브러리의 템플릿과 마찬가지로 문자 특성을 지정 하는 템플릿 매개 변수를 사용 하 여 동작을 사용자 지정할 수 있습니다.

- 를 사용 하 여 DLL에서 고유한 문자열 클래스를 내보낼 때 `CStringT` 컴파일러는 기본 클래스도 자동으로 내보냅니다 `CString` . `CString`는 자체 템플릿 클래스 이기 때문에, 컴파일러가 DLL에서 가져온 것을 인식 하지 않는 한 사용 시 컴파일러에 의해 인스턴스화될 수 있습니다 `CString` . Visual C++ 6.0에서 Visual C++ .NET으로 프로젝트를 마이그레이션한 경우 `CString` `CString` DLL에서 가져온와 로컬로 인스턴스화된 버전의 충돌로 인해 곱하기 정의에 대해 링커 기호 오류가 표시 될 수 있습니다. 이 작업을 수행 하는 적절 한 방법은 아래에 설명 되어 있습니다.

다음 시나리오에서는 링커가 정의 된 여러 클래스에 대 한 기호 오류를 생성 합니다. `CString`MFC 확장 DLL에서 파생 클래스 ()를 내보내는 경우를 가정 합니다 `CMyString` .

[!code-cpp[NVC_MFC_DLL#6](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_1.cpp)]

소비자 코드는와를 혼합 하 여 사용 `CString` `CMyString` 합니다. "MyString. h"는 미리 컴파일된 헤더에 포함 되지 않으며 일부 사용은 `CString` 표시 되지 않습니다 `CMyString` .

`CString`및 `CMyString` 클래스를 별도의 소스 파일 Source1 및 소스 2에 사용 한다고 가정 합니다. Source1에서는 `CMyString` 및 #include MyString. h를 사용 합니다. 소스 2에서 `CString` 를 사용 하지만 MyString을 #include 하지 않습니다. 이 경우 링커에서는 `CStringT` 곱하기로 정의 됩니다. 이는 `CString` 를 내보내는 DLL에서 가져온 `CMyString` 후 템플릿을 통해 컴파일러에 의해 로컬로 인스턴스화된 경우에 발생 `CStringT` 합니다.

이 문제를 해결 하려면 다음을 수행 합니다.

`CStringA` `CStringW` MFC90.DLL에서 및 (및 필요한 기본 클래스)를 내보냅니다. MFC를 포함 하는 프로젝트는 `CStringA` `CStringW` 이전 mfc 구현과 같이 항상 및를 내보낸 mfc DLL을 사용 합니다.

그런 다음 아래와 같이 템플릿을 사용 하 여 내보낼 수 있는 파생 클래스를 만듭니다 `CStringT` `CStringT_Exported` . 예를 들면 다음과 같습니다.

[!code-cpp[NVC_MFC_DLL#7](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_2.cpp)]

AfxStr에서 다음과 `CString` 같이 이전, `CStringA` 및 typedef를 바꿉니다 `CStringW` .

[!code-cpp[NVC_MFC_DLL#8](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_3.cpp)]

몇 가지 주의할 점이 있습니다.

- `CStringT`이로 인해 ATL 전용 프로젝트가 특수 한 클래스를 내보내도록 하 게 되므로 자체를 내보내지 않아야 합니다 `CStringT` .

- 에서 내보낼 수 있는 파생 클래스를 사용 하면 `CStringT` 기능을 다시 구현 하는 것이 최소화 `CStringT` 됩니다. 추가 코드는 생성자를 기본 클래스로 전달 하는 것으로 제한 됩니다 `CStringT` .

- `CString`, `CStringA` 및는 `CStringW` `__declspec(dllexport/dllimport)` MFC 공유 DLL을 사용 하 여 빌드하는 경우에만 표시 되어야 합니다. MFC 정적 라이브러리를 사용 하 여 연결 하는 경우 이러한 클래스를 내보낸 것으로 표시 하면 안 됩니다. 그렇지 않으면 사용자 Dll 내부에서, 및를 내부적으로 사용 하 여 `CString` `CStringA` 내보낸 것 `CStringW` 으로 표시 됩니다 `CString` .

## <a name="related-topics"></a>관련 항목

[CStringT 클래스](../atl-mfc-shared/reference/cstringt-class.md)

## <a name="see-also"></a>참고 항목

[CStringT 사용](../atl-mfc-shared/using-cstringt.md)<br/>
[CString 사용](../atl-mfc-shared/using-cstring.md)
