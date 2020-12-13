---
description: '자세히 알아보기: 컬렉션 및 열거자 인터페이스에 대 한 디자인 원칙'
title: 컬렉션 및 열거자 인터페이스 디자인 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- enumerator interfaces
- collection interfaces
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
ms.openlocfilehash: effd2cce775ef926befc89bb6b72a976d85bdf23
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148007"
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>컬렉션 및 열거자 인터페이스에 대 한 디자인 원칙

각 인터페이스 유형에는 다음과 같은 다양 한 디자인 원칙이 있습니다.

- 컬렉션 인터페이스는 메서드를 통해 컬렉션의 *단일* 항목에 대 한 *임의* 액세스를 제공 하 `Item` 고, 클라이언트에서 속성을 통해 컬렉션에 있는 항목 수를 검색 하 `Count` 고, 클라이언트에서 항목을 추가 및 제거할 수 있습니다.

- 열거자 인터페이스는 컬렉션의 *여러* 항목에 대 한 *직렬* 액세스를 제공 하며, 클라이언트가 컬렉션에 있는 항목 수 (열거자가 항목을 반환 하지 않을 때까지)를 검색 하는 것을 허용 하지 않으며, 항목을 추가 하거나 제거 하는 방법을 제공 하지 않습니다.

각 인터페이스 형식은 컬렉션의 요소에 대 한 액세스를 제공 하는 데 다른 역할을 수행 합니다.

## <a name="see-also"></a>참고 항목

[컬렉션 및 열거자](../atl/atl-collections-and-enumerators.md)
