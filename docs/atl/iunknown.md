---
description: '자세히 알아보기: IUnknown'
title: IUnknown
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
ms.openlocfilehash: ddfd35155162275885a1c0c842b4589fa6773a4a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152648"
---
# <a name="iunknown"></a>IUnknown

[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 은 다른 모든 COM 인터페이스의 기본 인터페이스입니다.  이 인터페이스는 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)), [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)및 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)의 세 가지 메서드를 정의 합니다. [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) 를 통해 인터페이스 사용자는 개체에 해당 인터페이스에 대 한 포인터를 요청할 수 있습니다. [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) 및 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) 는 인터페이스에 대 한 참조 계산을 구현 합니다.

## <a name="see-also"></a>참고 항목

[COM 소개](../atl/introduction-to-com.md)<br/>
[IUnknown 및 인터페이스 상속](/windows/win32/com/iunknown-and-interface-inheritance)
