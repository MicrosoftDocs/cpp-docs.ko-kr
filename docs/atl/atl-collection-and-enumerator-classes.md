---
description: '자세한 정보: ATL 컬렉션 및 열거자 클래스'
title: ATL 컬렉션 및 열거자 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
ms.openlocfilehash: b1f30aabb4908b0299a927f92a6d5ee4e9370a09
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166046"
---
# <a name="atl-collection-and-enumerator-classes"></a>ATL 컬렉션 및 열거자 클래스

ATL에서는 컬렉션과 열거자를 구현 하는 데 도움이 되는 다음 클래스를 제공 합니다.

|클래스|설명|
|-----------|-----------------|
|[ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)|컬렉션 인터페이스 구현|
|[IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)|열거자 인터페이스 구현 (c + + 표준 라이브러리 호환 컨테이너에 저장 된 데이터를 가정)|
|[CComEnumImpl](../atl/reference/ccomenumimpl-class.md)|열거자 인터페이스 구현 (배열에 저장 된 데이터를 가정)|
|[CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)|열거자 개체 구현 (사용 `IEnumOnSTLImpl` )|
|[CComEnum](../atl/reference/ccomenum-class.md)|열거자 개체 구현 (사용 `CComEnumImpl` )|
|[_Copy](../atl/atl-copy-policy-classes.md)|정책 클래스 복사|
|[_CopyInterface](../atl/atl-copy-policy-classes.md)|정책 클래스 복사|
|[CAdapt](../atl/reference/cadapt-class.md)|어댑터 클래스 (  `CComPtr` `CComQIPtr` `CComBSTR` c + + 표준 라이브러리 컨테이너에, 및을 (를) 저장할 수 있도록 하 &연산자를 숨깁니다.)|

## <a name="see-also"></a>참고 항목

[컬렉션 및 열거자](../atl/atl-collections-and-enumerators.md)
