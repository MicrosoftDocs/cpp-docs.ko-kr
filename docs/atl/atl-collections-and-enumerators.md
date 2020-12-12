---
description: '자세한 정보: ATL 컬렉션 및 열거자'
title: ATL 컬렉션 및 열거자
ms.date: 11/04/2016
helpviewer_keywords:
- enumerator interfaces
- collections, ATL classes
- enumerators, ATL classes
- collection interfaces
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
ms.openlocfilehash: 92e9ab3df52219812d72ae5cb811f57a3ecf4fad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166007"
---
# <a name="atl-collections-and-enumerators"></a>ATL 컬렉션 및 열거자

는 `collection` 데이터 항목 그룹 (원시 데이터 또는 기타 개체)에 대 한 액세스를 허용 하는 인터페이스를 제공 하는 COM 개체입니다. 개체 그룹에 대 한 액세스를 제공 하는 표준을 따르는 인터페이스를 *컬렉션 인터페이스* 라고 합니다.

최소한 컬렉션 인터페이스는 `Count` 컬렉션의 항목 수를 반환 하는 속성, `Item` 인덱스를 기반으로 컬렉션에서 항목을 반환 하는 속성 및 `_NewEnum` 컬렉션에 대 한 열거자를 반환 하는 속성을 제공 해야 합니다. 필요에 따라 컬렉션 인터페이스는 `Add` 및 `Remove` 메서드를 제공 하 여 컬렉션에서 항목을 삽입 하거나 삭제할 수 있으며, 메서드를 사용 하 여 `Clear` 모든 항목을 제거할 수 있습니다.

는 `enumerator` 컬렉션의 항목을 반복 하기 위한 인터페이스를 제공 하는 COM 개체입니다. 열거자 인터페이스는,, 및의 네 가지 필수 메서드를 통해 컬렉션의 요소에 대 한 직렬 액세스를 제공 `Next` `Skip` `Reset` `Clone` 합니다.

[IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) 인터페이스와 같은 참조 콘텐츠를 읽어 열거자 인터페이스에 대해 자세히 알아볼 수 있습니다.

## <a name="in-this-section"></a>섹션 내용

[ATL 컬렉션 및 열거자 클래스](../atl/atl-collection-and-enumerator-classes.md)<br/>
컬렉션과 열거자를 구현 하는 데 도움이 되는 ATL 클래스에 대해 간략하게 설명 하 고 링크를 제공 합니다.

[컬렉션 및 열거자 인터페이스에 대 한 디자인 원칙](../atl/design-principles-for-collection-and-enumerator-interfaces.md)<br/>
각 인터페이스 형식에 대 한 다양 한 디자인 원칙을 설명 합니다.

[C + + 표준 Library-Based 컬렉션 구현](../atl/implementing-an-stl-based-collection.md)<br/>
C + + 표준 라이브러리 기반 컬렉션의 구현 과정을 안내 하는 확장 된 예제입니다.

## <a name="related-sections"></a>관련 단원

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
액티브 템플릿 라이브러리를 사용하여 프로그래밍하는 방법에 대한 개념 항목의 링크를 제공합니다.

[이 컬렉션 샘플](../overview/visual-cpp-samples.md)<br/>
및의 사용 `ICollectionOnSTLImpl` `CComEnumOnSTL` 방법과 사용자 지정 복사 정책 클래스의 구현 방법을 보여 주는 샘플입니다.

## <a name="see-also"></a>참고 항목

[개념](../atl/active-template-library-atl-concepts.md)
