---
description: '자세한 정보: 주소 스토리지'
title: 주소 스토리지
ms.date: 11/04/2016
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
ms.openlocfilehash: 8f0b51370659d7a23739d75f53492d171c17e422
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296695"
---
# <a name="storage-of-addresses"></a>주소 스토리지

주소에 필요한 스토리지의 크기 및 주소의 의미는 컴파일러의 구현에 따라 다릅니다. 다른 형식에 대한 포인터가 동일한 길이가 되도록 보장되지 않습니다. 따라서 **sizeof(char \*)** 가 **sizeof(int \*)** 와 반드시 일치하는 것은 아닙니다.

**Microsoft 전용**

Microsoft C 컴파일러의 경우 **sizeof(char \*)** 는 **sizeof(int \*)** 와 일치합니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[포인터 선언](../c-language/pointer-declarations.md)
