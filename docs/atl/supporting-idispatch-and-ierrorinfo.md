---
description: '자세히 알아보기: IDispatch 및 IErrorInfo 지원'
title: IDispatch 및 IErrorInfo 지원
ms.date: 11/04/2016
helpviewer_keywords:
- ISupportErrorInfoImpl method
- IErrorInfo class suppor in ATL
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
ms.openlocfilehash: 4622c8811fafc9512400345e5876dd24c466bc93
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138452"
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>IDispatch 및 IErrorInfo 지원

[IDispatchImpl](../atl/reference/idispatchimpl-class.md) 템플릿 클래스를 사용 하 여 `IDispatch Interface` 개체의 이중 인터페이스 부분에 대 한 기본 구현을 제공할 수 있습니다.

개체가 인터페이스를 사용 하 여 `IErrorInfo` 클라이언트에 게 오류를 보고 하는 경우 개체는 인터페이스를 지원 해야 합니다 `ISupportErrorInfo Interface` . [은 isupporterrorinfoimpl](../atl/reference/isupporterrorinfoimpl-class.md) 템플릿 클래스는 개체에 오류를 생성 하는 단일 인터페이스만 있는 경우이를 구현 하는 쉬운 방법을 제공 합니다.

## <a name="see-also"></a>참고 항목

[ATL COM 개체의 기본 사항](../atl/fundamentals-of-atl-com-objects.md)
