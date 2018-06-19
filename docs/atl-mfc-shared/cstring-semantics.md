---
title: CString 의미 체계 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- semantics in Cstring
- CString objects, assignment semantics
- assignment statements, assigning CString objects
ms.assetid: d4023480-526f-499a-85f6-324b4de5b85f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1765f1f7f4103b1b2cfe6012b42ebef12f8863f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356581"
---
# <a name="cstring-semantics"></a>CString 의미 체계
경우에 [CString](../atl-mfc-shared/reference/cstringt-class.md) 개체는 증가할 수 있는 동적 개체, 기본 제공 기본 유형 및 간단한 클래스와 마찬가지로 작동 합니다. 각 `CString` 개체는 고유한 값을 나타냅니다. `CString` 문자열에 대 한 포인터가 아니라 실제 문자열로 개체의 생각해 야 합니다.  
  
 하나를 할당 **CString** 개체를 다른 개체입니다. 그러나 경우 하나를 수정 하면 두 `CString` 개체를 다른 `CString` 개체가 수정 되지 않으면 다음 예제에서와 같이:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#188](../atl-mfc-shared/codesnippet/cpp/cstring-semantics_1.cpp)]  
  
 예제에서는 참고 하는 두 `CString` 동일한 문자열 나타내기 때문에 개체 "같음" 간주 됩니다. `CString` 클래스 같음 연산자를 오버 로드 (`==`) 두 개를 비교 하려면 `CString` 개체 id (주소) 하는 대신 해당 값 (내용)에 기반 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [문자열 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

