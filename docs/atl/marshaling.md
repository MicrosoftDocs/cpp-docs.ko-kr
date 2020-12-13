---
description: '자세히 알아보기: 마샬링'
title: 마샬링
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 2931bd9ab5e2fb8376ced44dd519a6de107be88e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152635"
---
# <a name="marshaling"></a>마샬링

마샬링의 COM 기술은 한 프로세스의 개체에 의해 노출 된 인터페이스를 다른 프로세스에서 사용할 수 있도록 합니다. 마샬링에서 COM은 코드를 제공 하거나 인터페이스 구현자에서 제공 하는 코드를 사용 하 여 다른 컴퓨터에서 실행 되는 프로세스에 대 한 프로세스 간에 이동할 수 있는 형식으로 메서드 매개 변수를 압축 하 고 다른 쪽 끝에서 해당 매개 변수의 압축을 풉니다. 마찬가지로 COM은 호출에서 반환 될 때 이와 동일한 단계를 수행 해야 합니다.

> [!NOTE]
> 개체에서 제공 하는 인터페이스가 개체와 동일한 프로세스에서 사용 되는 경우에는 일반적으로 마샬링이 필요 하지 않습니다. 그러나 스레드 간에 마샬링이 필요할 수 있습니다.

## <a name="see-also"></a>참고 항목

[COM 소개](../atl/introduction-to-com.md)<br/>
[마샬링 정보](/windows/win32/com/marshaling-details)
