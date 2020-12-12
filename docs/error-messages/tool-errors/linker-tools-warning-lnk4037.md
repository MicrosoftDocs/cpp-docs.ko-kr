---
description: '자세한 정보: 링커 도구 경고 LNK4037'
title: 링커 도구 경고 LNK4037
ms.date: 10/04/2017
f1_keywords:
- LNK4037
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
ms.openlocfilehash: 78fd5ed9f8e2f82221b64053607846f1b8abc00a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331947"
---
# <a name="linker-tools-warning-lnk4037"></a>링커 도구 경고 LNK4037

>'*symbol*'이 없습니다. 무시

프로그램에서 찾을 수 없기 때문에 [/order](../../build/reference/order-put-functions-in-order.md) 옵션을 사용 하 여 데코레이팅된 이름 *기호* 를 정렬할 수 없습니다. 주문 지시 파일에서 *기호* 사양을 확인 합니다. 자세한 내용은 [/order (순서 대로 함수 배치)](../../build/reference/order-put-functions-in-order.md) 링커 옵션을 참조 하세요.

> [!NOTE]
> 정적 함수 이름이 공용 기호 이름이 아니므로 LINK에서 정적 함수를 정렬할 수 없습니다. **/Order** 를 지정 하면 주문 지시 파일에서 정적 또는 찾을 수 없는 각 기호에 대해이 링커 경고가 생성 됩니다.
