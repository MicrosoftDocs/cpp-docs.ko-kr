---
description: '자세한 정보: CString 의미 체계'
title: CString 의미 체계
ms.date: 11/04/2016
helpviewer_keywords:
- semantics in Cstring
- CString objects, assignment semantics
- assignment statements, assigning CString objects
ms.assetid: d4023480-526f-499a-85f6-324b4de5b85f
ms.openlocfilehash: 7c6dde91e7f87908c0c6bc2d49ff455eb79f6eb3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167047"
---
# <a name="cstring-semantics"></a>CString 의미 체계

[CString](../atl-mfc-shared/reference/cstringt-class.md) 개체가 확장할 수 있는 동적 개체 이더라도 기본 제공 기본 형식 및 단순 클래스 처럼 작동 합니다. 각 `CString` 개체는 고유한 값을 나타냅니다. `CString` 개체는 문자열에 대 한 포인터가 아닌 실제 문자열로 간주 되어야 합니다.

한 `CString` 개체를 다른 개체에 할당할 수 있습니다. 그러나 두 개체 중 하나를 수정 하는 경우 `CString` `CString` 다음 예제에 표시 된 것 처럼 다른 개체는 수정 되지 않습니다.

[!code-cpp[NVC_ATLMFC_Utilities#188](../atl-mfc-shared/codesnippet/cpp/cstring-semantics_1.cpp)]

예제에서 두 `CString` 개체는 동일한 문자열을 나타내므로 "equal"로 간주 됩니다. `CString`클래스는 같음 연산자 ()를 오버 로드 하 여 해당 `==` `CString` id (주소) 대신 해당 값 (내용)을 기반으로 두 개체를 비교 합니다.

## <a name="see-also"></a>참고 항목

[문자열 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)
